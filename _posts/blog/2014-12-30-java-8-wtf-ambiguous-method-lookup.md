---
layout: post
title: "Java 8 WTF: Ambiguous Method Lookup"
modified:
categories: blog
tags: []
image:
  feature:
date: 2014-12-30T15:39:07-05:00
comments: true
---

I am currently working on adding Java 7/8 support to [DoppioJVM](https://github.com/plasma-umass/doppio). In doing so, I am discovering some of the rather surprising JVM changes required to support Java 7+, and some interesting spec corner cases. In this blog post, I'll reveal some *very surprising* behavior involving a new Java 8 feature: Default interface methods!

{{ excerpt_separator }}

## Introduction to Default Interface Methods

Default interface methods let you include full method implementations in your interface definitions.
Classes that implement the interface do not need to explicitly implement these methods; they inherit the default implementation should the class not override it.
I believe that this is a positive change for Java.

For example, the following is now valid Java code; it prints `Bark!`:

{% highlight java %}
public class Test {
  public static void main(String[] args) {
    new Dog().makeNoise(); // Prints "Bark!"
  }
}
interface Animal {
  public String getNoise();
  default void makeNoise() {
    System.out.println(this.getNoise());
  }
}
class Dog implements Animal {
  public String getNoise() {
    return "Bark!";
  }
}
{% endhighlight %}

Using this functionality, Java 8 added a number of new methods to core Java interfaces *without* breaking existing code by providing default implementations, such as [`java.util.List.replaceAll`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html#replaceAll-java.util.function.UnaryOperator-).

In addition to this functionality, interfaces can now contain static methods, but this change is irrelevant to this blog post.

## JVM Changes Required

You may be surprised to hear that the above functionality requires changes at the Java Virtual Machine (JVM) level.
Previously, *all* methods invoked on an object could only be defined in the object's class or super classes.
Thus, method lookup for `invokevirtual` and `invokeinterface` instructions proceeds as follows in Java <8:

* Check the class of the object for a method with the given name and signature. If present, use that method.
* Else, recursively check the class's super types for a method with the given name and signature.
* If no suitable method is found, throw a `NoSuchMethodError`.

With default interface methods, the JVM now needs to search interfaces for method implementations.
Naturally, methods present in the object's class or super classes are prioritized over the default implementation in an interface.
Thus, method lookup for `invokevirtual` and `invokeinterface` instructions in Java 8+ now works as follows:

* Check the class of the object for a method with the given name and signature. If present, use that method.
* Else, recursively check the class's super types for a method with the given name and signature.
* Check the superinterfaces of the object for a method with the given name and signature.
* If no suitable method is found, throw a `NoSuchMethodError`.

This change appears to be relatively straightforward, but it introduces a subtle issue...

## Multiple Inheritance Troubles

The new lookup scheme introduces ambiguity when multiple interfaces provide default implementations of a method with the *same name and signature*.
Should the class and its super classes fail to provide an implementation for the desired method, how should the JVM prioritize one interface's default implementation over another?

The Java compiler writers knew this would be an issue, and applied a band-aid to prevent certain programs from compiling:

{% highlight java %}
public class JavaCHatesMe implements IFace1, IFace2 {

}
interface IFace1 {
  default void foo() {}
}
interface IFace2 {
  default void foo() {}
}
{% endhighlight %}

If you try to compile the above program, `javac` prints out the following error:

    $ javac JavaCHatesMe.java
    JavaCHatesMe.java:1: error: class JavaCHatesMe inherits unrelated defaults for foo() from types IFace1 and IFace2
    public class JavaCHatesMe implements IFace1, IFace2 {
      ^
      1 error

(It should be noted that without default methods, and with a concrete implementation of `foo` in `JavaCHatesMe`, the program compiles with no issue.)

However, this band-aid does not resolve the root problem! The following program compiles *just fine*:

{% highlight java %}
public class WTF {
  public static void main(String[] args) {
    ISpeak.test();
  }
}

interface ISpeak {
  default void speak() {
    System.out.println("ISpeak Speaking!");
  }

  public static void test() {
    new EmptySpeakImpl().speak();
    new EmptySpeakImplChild().speak();
  }
}

interface ISpeak2 extends ISpeak {
  default void speak() {
    System.out.println("ISpeak2 Speaking!");
  }
}

class EmptySpeakImpl implements ISpeak2 {}
class EmptySpeakImplChild extends EmptySpeakImpl implements ISpeak {}
{% endhighlight %}

In this example, `EmptySpeakImpl` implements the interface `ISpeak2`, and thus it clearly inherits `ISpeak2.speak()`.
However, `EmptySpeakImplChild` directly implements `ISpeak` and implements `ISpeak2` through its parent class, and thus its `speak()` method will be from either of those two interfaces.

Which `speak` implementation do you think `EmptySpeakImplChild` should inherit: `ISpeak.speak`, or `ISpeak2.speak`?
Common Java sense might indicate that the JVM should prioritize default interface methods specified in interfaces *directly implemented* by child classes over those inherited from interfaces implemented by parent classes.
According to this scheme, `EmptySpeakImplChild` should inherit `ISpeak.speak`, as it explicitly implements that interface.

However, Oracle's JVM, HotSpot, disagrees with this logic, as the above program prints out the following:

    $ java WTF
    ISpeak2 Speaking!
    ISpeak2 Speaking!

Why?

## Taking a Look at the JVM Specification

**EDIT: My interpretation below is incorrect, but I will leave it here for posterity. Please see the next section for an updated interpretation.**

A quick glance at the JVM specification reveals why this behavior occurs: *method lookup in Java 8 is officially ambiguous*.

From [JVM Spec §5.4.3.3](http://docs.oracle.com/javase/specs/jvms/se8/html/jvms-5.html#jvms-5.4.3.3):

> Otherwise, if any superinterface of C declares a method with the name and descriptor specified by the method reference that has neither its ACC_PRIVATE flag nor its ACC_STATIC flag set, **one of these is arbitrarily chosen and method lookup succeeds**.

By this definition of method resolution, both the proposed "common sense" behavior discussed above and HotSpot's behavior are valid by the spec.
In fact, one could simply invoke `Math.random()` in the process to decide among multiple choices.

While I expect Java developers to rarely encounter this corner case, it is rather disturbing to encounter a specification that explicitly introduces ambiguity into a core process. Since Java 8 is the *first* version of Java to include this behavior, this was an explicit decision on the part of the JVM standards committee rather than an after-the-fact discovery.

It would have been preferable to specify *some* order of preference, such as lexicographic ordering by name, order that interfaces are declared in the `class` file, etc. Even if the specified order of preference doesn't make sense to developers, it would allow alternative JVM implementations to have consistent behavior. I expect that programs that include this problematic behavior are doing so by accident, rather than conscious developer choice, and I would prefer that their program is portable across spec-compliant independent JVMs!

## Edit: Alternative JVM Specification Interpretation

User pron98 on reddit pointed out [that my interpretation of the JVM specification](http://www.reddit.com/r/programming/comments/2qula0/java_8_wtf_ambiguous_method_lookup/cn9th0y) may be incorrect, and that my example is not triggering the ambiguous behavior quoted above. In pron98's interpretation, the term *superinterfaces* in the specification refers solely to *direct superinterfaces* -- that is, interfaces directly implemented by a class C -- rather than *indirect superinterfaces*, which includes those that are inherited from C's parent classes.
Under this interpretation, default method bodies inherited from interfaces implemented on parent classes will *always* override default method bodies inherited from interfaces implemented on child classes.

pron98 links to a [section in the Java Language Specification](http://docs.oracle.com/javase/specs/jls/se8/html/jls-8.html#jls-8.4.8) which supports this interpretation:

> Note that it is possible for an inherited concrete method to prevent the inheritance of an abstract or default method. (Later we will assert that the concrete method overrides the abstract or default method "from C".) Also, it is possible for one supertype method to prevent the inheritance of another supertype method if the former "already" overrides the latter - this is the same as the rule for interfaces (§9.4.1), and prevents conflicts in which multiple default methods are inherited and one implementation is clearly meant to supersede the other.]

At first, this behavior seemed counterintuitive to me, as it appears to invert the inheritance hierarchy (e.g. methods in parent classes taking precedence over methods in child classes). However, *default* methods are used only when no other implementations exist, so if an implementation exists from a parent class, it makes some sense that the child class's default method will not be used when an implementation is first found in a parent class.

With all this said, method lookup **is still ambiguous** in the case that a class implements two interfaces with default method bodies for the same method. `javac` blocks all such programs from compiling, so Java programs are immune to the ambiguity, but non-Java languages that run on the JVM may still encounter the ambiguity.

## Edit 2: A little more complication...

I missed one more subtlety in the specification. Buried in the method resolution section is the term *maximally-specific superinterface methods* of `C`. When no implementation for an interface method exists, and the JVM goes searching for a default implementation, the definition of this term defines a priority on *certain* default interface methods.

This term is applicable to my example application with `ISpeak`. In particular, the default interface methods on subinterfaces are always prioritized over the default interface methods on their parents. Thus, since `EmptySpeakImplChild`'s parent implements `ISpeak2`, which is a subinterface of `ISpeak`, its default methods will *always* trump `ISpeak`'s default methods. As a result, my example is even less ambiguous than I thought it was!

## Next Post: `invokedynamic`

In my next post, I will dive into the murky world of `invokedynamic`: the specification, the implementation in OpenJDK, and the resulting consequences for JVM implementors.
