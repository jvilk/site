---
layout: post
title: "Java 8 Specification Bug: Default Interface Method Resolution"
modified:
categories: blog
tags: []
image:
feature:
date: 2015-01-01T14:39:05-05:00
comments: true
---

In a previous blog post, I pointed out some [rather surprising behavior](https://jvilk.com/blog/java-8-wtf-ambiguous-method-lookup/) involving default interface methods, and cases in which method resolution is ambiguous as specified by the JVM specification. However, after consulting with commenters on the corresponding [reddit](http://www.reddit.com/r/programming/comments/2qula0/java_8_wtf_ambiguous_method_lookup/cn9th0y) post, it is possible that that method resolution is never ambiguous, and the JVM specification is *incorrect*.

{{ excerpt_separator }}

I've written an email to the [JLS/JVM Specification Comments mailing list](http://mail.openjdk.java.net/mailman/listinfo/jls-jvms-spec-comments), which is a drop box for these sort of issues. I have no idea if they will get back to me or even discuss the issue, but I will post the full email here, with an addendum that describes how you can replicate the issue described in the email.

## Email to the JLS/JVM Committee

Hello,

I recently noticed a disagreement between the JLS and the JVMS for SE8 concerning the scenario where multiple direct superinterfaces of a class provide a default method for a method reference with the same name and signature. I believe this is a bug in the JVM specification, which specifies behavior that is not present in the reference implementation of the specification, and which differs from the behavior specified in the JLS.

The JVM specification states the following should occur in the section on method resolution, [§5.4.3.3](http://docs.oracle.com/javase/specs/jvms/se8/html/jvms-5.html#jvms-5.4.3.3), should there be no single maximally-specific default method (meaning, there are multiple) (emphasis mine):

> Otherwise, if any superinterface of `C `declares a method with the name and descriptor specified by the method reference that has neither its `ACC_PRIVATE` flag nor its `ACC_STATIC` flag set, **one of these is arbitrarily chosen and method lookup succeeds**.

However, the JLS specification states the following in the section on Interface Method Declarations in the binary compatibility chapter, [§13.5.6](http://docs.oracle.com/javase/specs/jls/se8/html/jls-13.html#jls-13.5.6):

> Adding a default method, or changing a method from abstract to default, does not break compatibility with pre-existing binaries, but may **cause an `IncompatibleClassChangeError` if a pre-existing binary attempts to invoke the method**.

This section of the JLS contains a full example that exemplifies the specification bug I am describing in this email. In particular, the JLS states:

> If `Cowboy` is recompiled but not `CowboyArtist`, then running the new binary with the existing binary for `CowboyArtist` will link without error **but cause an `IncompatibleClassChangeError` when main attempts to invoke `draw()`**.

However, this behavior description is in contrast to the JVM specification, which claims that one of the draw methods should be arbitrarily chosen and invoked.

Using separate compilation on the example, I verified that the JVM does, in fact, throw an `IncompatibleClassChangeError`, which disagrees with the behavior specified in the JVMS:

    $ java example/CowboyArtist
    Exception in thread "main" java.lang.IncompatibleClassChangeError: Conflicting default methods: example/Cowboy.draw example/Painter.draw
    at example.CowboyArtist.draw(CowboyArtist.java)
    at example.CowboyArtist.main(CowboyArtist.java:6)

Since this behavior originates in the JVM, rather than in the bytecode produced from the Java Compiler, it should be included in the JVM specification.

Thus, to fix this specification bug, I propose that the quoted section of the JVMS from the method resolution section be replaced with the following text:

> Otherwise, if there are multiple maximally-specific superinterface methods of `C` for the name and descriptor specified by the method reference, method resolution throws an `IncompatibleClassChangeError`.

I believe the above text captures the behavior of the current reference implementation, and is in line with the JLS.

Let me know if you have any questions, comments, or if you find a mistake in my reasoning above. It is very possible that I am missing a subtlety.

Thanks for reading!

John

## Replicating the Behavior

If you want to try this at home, you'll need to install the [Java 8 JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). To provoke the behavior, we'll need to use *separate compilation*, since the Java Compiler will not compile code if it can prove at compile time that a class implements two interfaces that provide a default method with the same name and signature.

In Java, *separate compilation* means that multiple components of an application are compiled independently, and thus it is possible that the application will run with a version of a component that it was not compiled against. Normally, Java programs are run against the same code that they are compiled against. For example, if you compile your program against JUnit 4.10, you will most likely run your program against JUnit 4.10. However, it is possible to run the code against alternative versions of JUnit, such as JUnit 4.11, without issue.

In any case, interesting problems can occur when your code is run against versions of classes that they were not compiled with. We abuse this flexibility to force a scenario where a class implements two interfaces that provide the same default method.

First, create the following files:

{% highlight java %}
// In example/Cowboy.java:
package example;

public interface Cowboy {
}

// In example/Painter.java:
package example;

public interface Painter {
  default void draw() {
    System.out.println("Here's a picture...");
  }
}

// In example/CowboyArtist.java:
package example;
import example.*;

public class CowboyArtist implements Cowboy, Painter {
  public static void main(String[] args) {
    new CowboyArtist().draw();
  }
}
{% endhighlight %}

Next, compile a first version of the program, and verify that it runs properly:

    $ javac example/CowboyArtist.java
    $ java example.CowboyArtist
    Here's a picture...

Next, modify `example/Cowboy.java` so that it implements `draw`:
{% highlight java %}
package example;

public interface Cowboy {
  default void draw() {
    System.out.println("Bang!");
  }
}
{% endhighlight %}

Recompile `Cowboy` alone, and try to run the program. Notice that it throws an `IncompatibleClassChangeError`:

    $ javac example/Cowboy.java
    $ java example.CowboyArtist
    Exception in thread "main" java.lang.IncompatibleClassChangeError: Conflicting default methods: example/Cowboy.draw example/Painter.draw
    at example.CowboyArtist.draw(CowboyArtist.java)
    at example.CowboyArtist.main(CowboyArtist.java:6)

The crux of the issue that I describe in my email is that the JVM specification states that the JVM should arbitrarily choose to invoke either `example/Cowboy.draw` or `example/Painter.draw`, yet the Java Language Specification (JLS) states that the JVM should throw an `IncompatibleClassChangeError`. HotSpot, the JVM in OpenJDK, is the reference implementation of the specification. Since HotSpot inplements the behavior in the JLS, it appears that the JVM specification is incorrect and should be updated to reflect the behavior in HotSpot.

## Life Lessons Learned

What I've learned from all of this is that blogging about all of the odd JVM corner cases I have to explore in creating [DoppioJVM](https://github.com/plasma-umass/doppio) can bring to light some of the complications of adding features to a well-entrenched language like Java as commenters step forward and share their expertise. I hope you all continue to correct me as I stumble through understanding the JVM specification, and wonder how certain sections came to be.

With that said, I'm off to read more about `invokedynamic`, which I'm currently fighting to get right in [DoppioJVM](https://github.com/plasma-umass/doppio). :)
