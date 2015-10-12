---
layout: page
title: About Me
image:
  feature: about_photo.jpg
excerpt: "John Vilk is a fifth year PhD student at UMass Amherst."
modified: 2014-08-08T19:44:38.564948-04:00
---

I am a fifth year PhD student at the University of Massachusetts Amherst. I work in the [PLASMA](http://www.cs.umass.edu/~plasma/) lab with [Emery Berger](http://emeryberger.com/). Feel free to [contact me](../contact/) if you want to get in touch!

* Table of Contents
{:toc}

## Research

I am interested in bringing general purpose programming and novel debugging techniques to constrained programming environments, such as the web browser.
These environments lack common operating system abstractions and constrain execution in ways that preclude reusing code written for general purpose programming environments.
At the same time, these programs exhibit characteristics that can be exploited to produce low-overhead debugging tools.

> **Mesovirtualization: Enabling Lightweight Virtual Machines**
>
> We introduce mesovirtualization, a new technique for running lightweight VMs in the cloud.
> Mesovirtualization leverages the fact that many cloud applications run atop a managed runtime; by treating the managed runtime interface as the definition for a virtualized hardware environment, we capture rich, high-level application semantics while ignoring large amounts of low-level architectural state that traditional virtualization approaches have to manage.
> The resulting VMs are orders of magnitude smaller than traditional Xen images.
>
> Mesovirtualization enables efficient implementations of VM services that have traditionally been expensive to support.
> For example, we demonstrate that mesovirtualization makes VM snapshotting and event logging cheap; using these two primitives, we construct the first time travel debugger which is fast enough to run on production systems.
>Virtual machines are useful for many tasks. For example, the virtualization layer acts as a convenient boundary for encapsulating program state, letting users snapshot, migrate, and resume complex, multi-level software applications.
> The virtual machine interface (VMI) also provides a natural introspection point for logging nondeterministic events that affect program execution.
> These event logs enable a variety of security and debugging analyses.
>
> This work is currently in submission.
>
> * [Channel9: Time-Travel Debugging for JavaScript/HTML (Video)](https://channel9.msdn.com/blogs/Marron/Time-Travel-Debugging-for-JavaScriptHTML)
> {: .hlist}
{: .project}

> **SurroundWeb: Mitigating Privacy Concerns in a 3D Web Browser**
>
> Immersive experiences that mix digital and real-world objects are becoming reality, but they raise serious privacy concerns as they require real-time sensor input. SurroundWeb is the first 3D web browser that provides the novel functionality of rendering web content onto a room while tackling many of the inherent privacy challenges. Following the principle of least privilege, we propose three abstractions for immersive rendering:
>
> 1. The *room skeleton* lets applications place content in response to the physical dimensions and locations of renderable surfaces in a room.
> 2. The *detection sandbox* lets applications declaratively place content near recognized objects in the room without revealing if the object is present.
> 3. *Satellite screens* let applications display content across devices registered with SurroundWeb.
>
> We implement these abstractions in a prototype system, and demonstrate that a wide range of immersive experiences can be implemented  with acceptable performance. SurroundWeb will appear at [IEEE Security and Privacy 2015](http://www.ieee-security.org/TC/SP2015/).
>
> * [IEEE S&P '15 Paper](https://jvilk.com/assets/pdf/oakland15.pdf)
> * [TechFair 2014 (Video)](http://research.microsoft.com/apps/video/?id=212669)
> * [BBC Coverage (Video)](http://www.bbc.com/news/technology-27243375)
> {: .hlist}
{: .project}

> **Doppio: Breaking the Browser Language Barrier**
>
> Doppio is a JavaScript-based runtime system that makes it possible to run unaltered applications written in general-purpose languages directly inside the browser. Doppio provides a wide range of runtime services, including a file system that enables local and external (cloud-based) storage, an unmanaged heap, sockets, blocking I/O, and multiple threads. We demonstrate Doppio's usefulness with two case studies: we extend Emscripten with Doppio, letting it run an unmodified C++ application in the browser with full functionality, and present DoppioJVM, an interpreter that runs unmodified JVM programs directly in the browser. This work appeared at [PLDI 2014](http://conferences.inf.ed.ac.uk/pldi2014/), won the [Distinguished Artifact Award](http://pldi14-aec.cs.brown.edu/), and was selected as a [SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)!
>
> DoppioJVM is currently used by the University of Illinois at [CodeMoo.com](http://codemoo.com/) to teach children how to program in Java, and components of Doppio are used by the [MS-DOS Collection](https://archive.org/details/softwarelibrary_msdos_games/v2) at the [Internet Archive](https://archive.org/).
>
> * [Demo](http://doppiojvm.org/)
> * [Source Code](https://github.com/plasma-umass/doppio)
> * [PLDI '14 Paper](http://dl.acm.org/citation.cfm?id=2594293) ([Alt. Link](https://plasma-umass.github.io/doppio-demo/paper.pdf))
> * [Talk @ Microsoft Research (Video)](http://research.microsoft.com/apps/video/default.aspx?id=238749&l=i)
> {: .hlist}
{: .project}

## Side Projects

Occasionally, I find the time to work on some fun side projects.

> **MS-DOS Collection at the Internet Archive**
>
> The [MS-DOS Collection](https://archive.org/details/softwarelibrary_msdos_games/v2) at the [Internet Archive](https://archive.org/) relies on [Doppio's file system](https://github.com/jvilk/browserfs) to make a large collection of DOS games playable in the browser.
> I worked with archive employees to integrate the file system appropriately, and to address a complex Cross-origin Resource Sharing (CORS) issue that prevented the initial deployment from working in Internet Explorer and Safari.
>
> * [Homepage](https://archive.org/details/softwarelibrary_msdos_games/v2)
> {: .hlist}
{: .project}

> **JSMESS: Multi Emulator Super System in JavaScript**
>
> The [JSMESS](http://jsmess.textfiles.com/) project aims to port the [Multi Emulator Super System (MESS)](http://mess.org/) to JavaScript to enable accurate and embeddable vintage computer and video game console emulators in the browser. This project has enabled the [Internet Archive](http://archive.org/) to provide its visitors with interactive demos of vintage and historical software for educational purposes. We use [Emscripten](https://github.com/kripken/emscripten) along with tweaks to the MESS source code to accomplish this feat.
>
> * [Homepage and Demo](http://jsmess.textfiles.com/)
> * [Historical Software Collection](https://archive.org/details/historicalsoftware)
> * [Console Living Room](https://archive.org/details/consolelivingroom)
> * [Source Code](https://github.com/jsmess/jsmess)
> {: .hlist}
{: .project}

> **SDL Joystick Support in Emscripten**
>
> I augmented [Emscripten](https://github.com/kripken/emscripten/)'s SDL emulation with support for the SDL Joystick API using the [HTML5 Gamepad API](http://www.w3.org/TR/gamepad/). As a result, SDL applications ported to the web with Emscripten, such as JSMESS, will function appropriately with USB gamepads. This code has been integrated into the Emscripten code base, and is present in Emscripten releases since v1.7.3.
>
> {: .hlist}
{: .project}

## Experience

* **Research Intern**, Microsoft Research, Summer 2015.
  * *Mentors*: [James Mickens](http://www.seas.harvard.edu/directory/mickens) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
* **Research Intern**, Microsoft Research, Summer 2014.
  * *Mentors*: [James Mickens](http://www.seas.harvard.edu/directory/mickens) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
* **Research Intern**, Microsoft Research, Summer 2013.
  * *Mentor*: [David Molnar](http://research.microsoft.com/en-us/people/dmolnar/)
* **Software Engineering Intern**, Google, Summer 2012.
* **Research Assistant**, University of Massachusetts, 2011 to present.
* **Research Intern**, MIT Lincoln Laboratory, Summer 2011.
* **Software Engineering Intern**, SoftArtisans Inc., Summer 2010.
{: .simplelist}

## Education

* **M.S. in Computer Science**, University of Massachusetts, 2014.
* **B.S. in Computer Science**, Worcester Polytechnic Institute, 2011.
{: .simplelist}

## Awards

* **IEEE Security & Privacy Student Travel Grant Recipient**, IEEE S&P 2015.
* **Facebook Fellowship** for the 2015-2016 and 2016-2017 academic years, February 2015.
* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [Doppio](http://dl.acm.org/citation.cfm?id=2594293), November 2014.
* **USENIX Student Grant Recipient** for travel to OSDI 2014.
* **Distinguished Artifact Award** for [Doppio: Breaking the Browser Language Barrier](http://github.com/plasma-umass/doppio), PLDI 2014.
* **SIGPLAN PAC Student Travel Grant Recipient** for travel to PLDI 2014.
* **Programming Languages Mentoring Workshop Travel Grant Recipient**, POPL 2012.
* **Upsilon Pi Epsilon computer science honor society member**, inducted into the WPI chapter in 2011.
* **Salisbury Prize**, WPI, 2011.
  * Awarded for completing all of my requirements at WPI "faithfully, industriously, and with distinguished attainment".
* **Dr. Neil G. Sullivan Memorial Award**, WPI, 2010.
  * Awarded annually to three junior undergraduates in recognition of their demonstrated ability and promise.
* **WPI Student Employee of the Year Nominee**, WPI, 2009-2010.
* **Charles O' Thompson Scholar**, WPI, 2008.
  * Recognizes outstanding performance by first-year undergraduate students.
{: .simplelist}

## Professional Activities

* **Mentor**, [Computing Beyond the Double Bind Mentoring Network](https://www.terc.edu/display/Projects/Computing+Beyond+the+Double+Bind%3A+Women+of+Color+in+Computing+Education+and+Careers), 2015-present.
* **Member**, IEEE, 2015-present.
* **Member**, USENIX, 2014-present.
* **Graduate Representative**, academic year 2014-2015, University of Massachusetts School of Computer Science.
  * Graduate representatives attend and vote during faculty meetings, and form a bridge between the graduate students and the faculty as a whole.
* **Student Volunteer**, OOPSLA 2014.
* **Artifact Evaluation Committee Member**: OOPSLA 2015, PLDI 2015, OOPSLA 2014.
* **External Reviewer:** USENIX Security 2014, PLDI 2014, OOPSLA 2012, MSPC 2012, HotPar 2012.
* **Member**, Association for Computing Machinery, 2008-present.
{: .simplelist}

## Teaching

* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2015.
  * *Students*: Muhammad Bhatti
* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2013.
  * *Students*: [Giles Lavelle](http://lavelle.co/) & [Braden McDorman](http://bmcdorman.cloudapp.net/)
{: .simplelist}
