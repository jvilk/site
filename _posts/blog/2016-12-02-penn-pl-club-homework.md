---
layout: post
title: "Penn PL Club Homework: Making the Browser Reasonable for Sane Programmers"
modified:
categories: blog
tags: []
image:
feature:
date: 2016-12-02T02:00:00-05:00
comments: false
---

*I am giving a talk at the [University of Pennsylvania's PL Club](https://www.cis.upenn.edu/~plclub/) next week,
and was given the opportunity to assign a bit of homework to the audience.
This blog post contains the content of that homework.*

{{ excerpt_separator }}

Before my talk, I want you to appreciate some of the difficulties involved in writing and debugging web apps.
If you have the time, I'd like you to run, tinker with, and think about some of the JavaScript code snippets below.
It will help you understand where my research is coming from.

## Basic JavaScript

*For this section, I recommend you [open your browser's Developer Tools](https://developers.google.com/web/tools/chrome-devtools/shortcuts#accessing_devtools)
to the Console, which is a REPL. All modern browsers have this feature. There, you can follow along with the examples.*

JavaScript is a high-level and dynamically typed programming language. When you write a web application, it must be written in or compile down to JavaScript.

It has some odd behavior due to implicit conversions:

{% highlight javascript %}
[] + [] // = "" (empty string)
[] + {} // = the string "[object Object]"
"hello" + 1 // = the string "hello1"
"hello" - 1 // = NaN (not a number)
{% endhighlight %}

There are two equality operators: `==` performs implicit conversions, `===` does not.

{% highlight javascript %}
'3' == 3 // true; implicitly converts 3 to '3'
'3' === 3 // false
3 === 3 // true
{% endhighlight %}

Objects are essentially maps from strings to properties, and you can define new properties at any time:

{% highlight javascript %}
var someObject = {
  // number
  foo: 3,
  // array
  bar: [1, 2, 3],
  baz: '3'
};
someObject.foo; // 3
someObject['foo']; // 3
someObject.newProperty = "hello"; // Creates a new object property
{% endhighlight %}

Objects can inherit properties from a prototype object:

{% highlight javascript %}
var someObject = {};
var someObjectPrototype =  {
  foo: 3
};
Object.setPrototypeOf(someObject, someObjectPrototype);
// Inherited field from prototype
someObject.foo; // 3
// Creates field foo on someObject, distinct from prototype's
// foo field!
someObject.foo = 4;
someObject.foo; // 4
someObjectPrototype.foo; // 3
{% endhighlight %}

Arrays are objects, too:

{% highlight javascript %}
var arr = ["hello"];

// You can add properties to arrays, like objects.
arr.newProperty = 3;

typeof(arr); // "object"
{% endhighlight %}

JavaScript has a loose definition of object types. To define a `Dog` class, you define a function called `Dog` and call it with `new`. The result is an object that identifies as a `Dog`:

{% highlight javascript %}
function Dog(name) {
  // 'this' points to the new Dog object you're constructing.
  this.name = name;
  this.animalType = "dog";
  this.sound = "woof";
}
// All Dog objects will have the prototype Dog.prototype,
// and thus will have the function getSound().
Dog.prototype.getSound = function() {
  return this.sound;
}

var charles = new Dog('Charles');
charles.getSound(); // 'woof'
charles instanceof Dog; // true
charles instanceof Object; //true
{% endhighlight %}

We can muck with `Dog` later to confuse `instanceof`, though:

{% highlight javascript %}
// Change Dog's prototype object.
Dog.prototype = Object;
// charles's prototype object is no longer
// equal to Dog.prototype, so instanceof returns
// false.
charles instanceof Dog; // false
{% endhighlight %}

This is just a small taste of the many oddities of JavaScript. Due to its dynamism, it is very easy to introduce bugs into your code.

## Event-driven Execution

In most traditional imperative programming languages, a program begins and ends in a single function (e.g., `main()`). If you pause the application at a debugger breakpoint, you can see a stack trace leading back to this main entrypoint.

JavaScript programs are not like this; instead, they are entirely *event-driven*. When a JavaScript library loads on a webpage, it subscribes to events it is interested in via *event handlers*. The browser triggers the relevant handler(s) when an event happens.

Browser APIs expose functionality via events wherever possible: user input, network requests, timers, storage interfaces, etc.

For example, the following code subscribes to clicks on a button, and lets the user know if they clicked the button after 5 seconds:

{% highlight javascript %}
var buttons = document.getElementsByTagName('button');
// Assumption: There's only one button on the page.
var button = buttons[0];
var clicked = false;
button.addEventListener('click', function() {
  clicked = true;
});
// Check if user clicked button after 5 seconds
// via a timer event.
setTimeout(function() {
  if (clicked) {
    alert("You clicked the button! :D");
  } else {
    alert("You didn't click the button. :(")
  }
}, 5000);
{% endhighlight %}
<a href="/images/pl-club-examples/button.html" target="_blank"><i>Run this code</i></a>

In JavaScript, *everything* is event-driven. You cannot opt out.
At the same time, JavaScript execution blocks the UI from updating or receiving user input.
As a result, a long-running event can *crash the browser tab*.

For example, the following code will crash your browser tab. You cannot click the button on the page. The browser will ask you if you want to kill the tab:

{% highlight html %}
<!doctype html>
<html>
<script type="text/javascript">
// Wrap in timer so button displays before
// we crash the tab.
setTimeout(function() {
  while (1) {
    // Infinite loop. :D
  }
}, 100);
</script>
<button>Try to click me. You can't.</button>

</html>
{% endhighlight %}
<a href="/images/pl-club-examples/crash.html" target="_blank"><i>Run this code (WARNING: crashes tab!)</i></a>

Web developers need to consciously avoid this problem. If an application needs to process a large amount of data (or do something else that is CPU intensive), it needs to space processing across multiple events to keep the webpage responsive.

## Events and Debugging

Events have many implications for debugging. If you pause the application at a debugger breakpoint, you will see a stack trace that leads back to the start of the current event, but you won't see the set of events that preceded it.

In the following contrived example, the breakpoint in `bar` will let you example a stack trace back to `foo`, but will not say anything about `baz` and its timer:

{% highlight javascript %}
var error = false;
function bar() {
  if (error) {
    // If you have developer tools open, the debugger statement triggers a breakpoint.
    debugger;
    alert("Error occurred!");
  }
}

function foo() {
  bar();
}

function baz() {
  error = true;
}

// Run baz after 50 milliseconds
setTimeout(baz, 50);
// Run foo after 5 seconds.
setTimeout(foo, 5000);
{% endhighlight %}
<a href="/images/pl-club-examples/events-debugging.html" target="_blank"><i>Try running `events-debugging.html` in Chrome</i></a>*, and [open developer tools](https://developers.google.com/web/tools/chrome-devtools/shortcuts#accessing_devtools) before the error alert occurs. It will open the debugger at the debugger statement.*

Events make it difficult to determine the origin of a bug. In this example, the "bug" occurs because `baz` sets `error` to true. In an actual application, bugs may manifest many events in the future from the source of the bug.

If the bug is hard to reproduce, a developer will spend much of their time reproducing the bug and testing hypotheses by setting breakpoints in various locations (or by liberally inserting `console.log` statements in the code).

## Race Conditions

JavaScript is single-threaded, but it is not without races. [Previous work has discussed some of these races in-depth.](https://dl.acm.org/citation.cfm?id=2254095)

There are two primary sources of races in JavaScript: those caused by event scheduling, and those caused by browser components executing in parallel with JavaScript execution. The latter are more subtle, and are not discussed by existing work on web application race detection.

### Event Scheduling

If you have ever programmed with asynchronous I/O, then you may be aware that you cannot rely on the order in which multiple outstanding I/O operations complete. Similarly, you cannot rely on a JavaScript program to execute events in the same order for every execution.

As an example, the following code will display the content of `data` when the user clicks the button. However, `data` isn't initialized until the timer fires, so if the user clicks the button prematurely, the webpage will display the message "undefined":

{% highlight javascript %}
var data;
var button = document.getElementsByTagName('button')[0];
button.addEventListener('click', function() {
  alert(data);
});
setTimeout(function() {
  data = "Welcome to this website!";
}, 2000);
{% endhighlight %}
<a href="/images/pl-club-examples/event-race.html" target="_blank"><i>Run this code</i></a>

The above example is contrived to keep these code snippets short, but these types of races are a common source of bugs!

Event scheduling-related races can be hard to find in more complicated web applications, and may only trigger in exceptional circumstances (e.g., a server is under heavy load, delaying requests).

### Browser Components

While JavaScript is single threaded, the web browser is *not*. Browsers attempt to parallelize what they can, and can update state that is visible to JavaScript in *parallel* with JavaScript execution. As a result, JavaScript code can race with other components in the browser.

To make the problem concrete, suppose that a web page uses CSS to make a `div` element periodically change its color. Further suppose that JavaScript code wishes to query its color:

{% highlight html %}
<style type="text/css">
@keyframes color_change {
  from { background-color: blue; }
  to { background-color: red; }
}
#picker { animation: color_change 5s infinite alternate; }
</style>
<div id="picker">
  Picker
</div>
<script type="text/javascript">
// Checks if element e has a blue background.
function isBlue(e) {
  var color = getComputedStyle(e).backgroundColor;
  return color === 'rgb(0, 0, 255)';
}

var div = document.getElementById('picker');
if (isBlue(div)) {
  // do something
}

// Observe that the animation continues when the program
// is paused at this breakpoint!
debugger;

if (isBlue(div)) {
  // do something
}

</script>
{% endhighlight %}
<a href="/images/pl-club-examples/component-race.html" target="_blank"><i>Run this code</i></a>

One might assume that if `isBlue(div)` returns true the first time that it would also return true the second time. However, this is not true. The `color_change` animation occurs in parallel with JavaScript, so `backgroundColor` changes while the script executes!

In addition to animations, network events can happen in parallel with JavaScript execution. For example, the `height` and `width` properties on an image are 0 until the image loads, and an image can load while JavaScript executes.

## Conclusion

After reading through this document and trying some of the code samples, I hope you understand some of the challenges involved in writing and debugging web applications. Keep these challenges in mind during my talk.

If any of the examples or explanations are unclear or if you have questions, [feel free to contact me](http://jvilk.com/contact/).

Thanks for reading!
