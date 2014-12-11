---
layout: page
title: About Me
image:
  feature: about_photo.jpg
excerpt: "John Vilk is a fourth year PhD student at UMass Amherst."
modified: 2014-08-08T19:44:38.564948-04:00
---

I am a fourth year PhD student at UMass Amherst. I work in the [PLASMA](http://www.cs.umass.edu/~plasma/) lab with [Emery Berger](http://emeryberger.com/). Feel free to [contact me](../contact/) if you want to get in touch!

* Table of Contents
{:toc}

## Research

I am interested in bringing general purpose programming to the web, including the resources that these programs require. To achieve this goal, my research brings existing operating system abstractions and programming languages into the web browser in a portable manner using JavaScript. My work enables developers to use existing and well-tested general purpose code in the browser environment.

<blockquote markdown="1" class="project">
**Doppio: Breaking the Browser Language Barrier**

Doppio is a JavaScript-based runtime system that makes it possible to run unaltered applications written in general-purpose languages directly inside the browser. Doppio provides a wide range of runtime services, including a file system that enables local and external (cloud-based) storage, an unmanaged heap, sockets, blocking I/O, and multiple threads. We demonstrate Doppio's usefulness with two case studies: we extend Emscripten with Doppio, letting it run an unmodified C++ application in the browser with full functionality, and present DoppioJVM, an interpreter that runs unmodified JVM programs directly in the browser. This work appeared at [PLDI 2014](http://conferences.inf.ed.ac.uk/pldi2014/), and won the [Distinguished Artifact Award](http://pldi14-aec.cs.brown.edu/)!

* [Demo](http://doppiojvm.org/)
* [Source Code](https://github.com/plasma-umass/doppio)
* [Full Paper](http://dl.acm.org/citation.cfm?id=2594293) ([Alt. Link](https://plasma-umass.github.io/doppio-demo/paper.pdf))
</blockquote>

<blockquote markdown="1" class="project">
**SurroundWeb: Least Privilege for Immersive "Web Rooms"**

As an intern at Microsoft Research, I worked with [David Molnar](http://research.microsoft.com/en-us/people/dmolnar/) and many others to build SurroundWeb. SurroundWeb is a 3D Browser that gives web pages the ability to display across multiple surfaces in a room, adapt their appearance to objects present in that room, and react to natural user input. SurroundWeb introduces two new abstractions: a Room Skeleton that enables least privilege for room rendering, and a Detection Sandbox that allows web pages to register content to show if an object is detected, but prevents the web server from knowing if the object is present. We demonstrate a range of previously proposed and novel experiences can be implemented in a least-privilege way using SurroundWeb.

* [Tech Report (In submission)](http://research.microsoft.com/apps/pubs/?id=209968)
</blockquote>

## Side Projects

Occasionally, I find the time to work on some fun side projects.

<blockquote markdown="1" class="project">
**JSMESS: Multi Emulator Super System in JavaScript**

The [JSMESS](http://jsmess.textfiles.com/) project aims to port the [Multi Emulator Super System (MESS)](http://mess.org/) to JavaScript to enable accurate and embeddable vintage computer and video game console emulators in the browser. This project has enabled the [Internet Archive](http://archive.org/) to provide its visitors with interactive demos of vintage and historical software for educational purposes. We use [Emscripten](https://github.com/kripken/emscripten) along with tweaks to the MESS source code to accomplish this feat.

* [Homepage and Demo](http://jsmess.textfiles.com/)
* [Internet Archive Historical Software Collection](https://archive.org/details/historicalsoftware)
* [Download](https://github.com/jsmess/jsmess)
</blockquote>

<blockquote markdown="1" class="project">
**SDL Joystick Support in Emscripten**

I augmented [Emscripten](https://github.com/kripken/emscripten/)'s SDL emulation with support for the SDL Joystick API using the [HTML5 Gamepad API](http://www.w3.org/TR/gamepad/). As a result, SDL applications ported to the web with Emscripten, such as JSMESS, will function appropriately with USB gamepads. This code has been integrated into the Emscripten code base, and is present in Emscripten releases since v1.7.3.

* [Simple Demo [FF and Chrome Only] ](http://people.cs.umass.edu/~jvilk/sdljoy/sdljoy.html)
</blockquote>

## Browser Bugs

While working on my research, I have discovered and reported a few browser bugs.

**Chrome**:

* [Heap snapshots not saved with file extension](https://code.google.com/p/chromium/issues/detail?id=154073)
* [Heap snapshots cannot be compared after saving and reloading](https://code.google.com/p/chromium/issues/detail?id=154084)
* [Loading multiple heap snapshots before viewing leads to odd behavior](https://code.google.com/p/chromium/issues/detail?id=154095)

**Safari**:

* [Typed arrays are not garbage collected.](https://bugs.webkit.org/show_bug.cgi?id=119049)
* [XMLHttpRequest Response is null when requesting empty file as ArrayBuffer](https://bugs.webkit.org/show_bug.cgi?id=123457)

## Experience

* **Research Intern**, Microsoft Research, Summer 2014.
* **Research Intern**, Microsoft Research, Summer 2013.
* **Software Engineering Intern**, Google, Summer 2012
* **Research Assistant**, University of Massachusetts, 2011 to present.
* **Research Intern**, MIT Lincoln Laboratory, Summer 2011
* **Software Engineering Intern**, SoftArtisans Inc., Summer 2010

## Awards

* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [Doppio](http://dl.acm.org/citation.cfm?id=2594293), November 2014.
* **Distinguished Artifact Award** for [DoppioJVM](http://github.com/plasma-umass/doppio), PLDI 2014.

## Teaching

* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2013.

## Education

* **M.S. in Computer Science**, University of Massachusetts, 2014.
* **B.S. in Computer Science**, Worcester Polytechnic Institute, 2011.
