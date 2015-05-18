---
layout: page
title: About Me
image:
  feature: about_photo.jpg
excerpt: "John Vilk is a fourth year PhD student at UMass Amherst."
modified: 2014-08-08T19:44:38.564948-04:00
---

I am a fourth year PhD student at the University of Massachusetts Amherst. I work in the [PLASMA](http://www.cs.umass.edu/~plasma/) lab with [Emery Berger](http://emeryberger.com/). Feel free to [contact me](../contact/) if you want to get in touch!

* Table of Contents
{:toc}

## Research

I am interested in bringing general purpose programming to the web, including the resources that these programs require. To achieve this goal, my research brings existing operating system abstractions and programming languages into the web browser in a portable manner using JavaScript. My work enables developers to use existing and well-tested general purpose code in the browser environment.

> **Lightweight JavaScript Virtual Machines**
>
>Virtual machines are useful for many tasks. For example, the virtualization layer acts as a convenient boundary for encapsulating program state, letting users snapshot, migrate, and resume complex, multi-level software applications. The virtual machine interface (VMI) also provides a natural introspection point for logging nondeterministic events that affect program execution. These event logs enable a variety of security and debugging analyses.
>
> Prior VMIs like Xen focus on providing strong and efficient isolation. In this paper, we describe a new approach called interrogative virtualization whose primary goal is to *efficiently capture application-level semantics* in order to *minimize the size of VM snapshots and event logs.* By raising the abstraction level of the VMI to that of the application of interest, interrogative VMs can safely ignore large portions of architectural state in the OS and the hardware. As a concrete demonstration, we introduce *JavaScript virtual machines*, and describe how a managed runtime, suitably extended to capture a small number of nontraditional events, defines an interrogative VMI whose virtual machines are an order of magnitude smaller than those of prior VMIs like Xen. We show that interrogative virtualization can retain standard VM security guarantees while still preserving small VM sizes by layering the interrogative VMI atop a traditional VMI like Xen. To demonstrate the utility of interrogative VMIs, we build MoveJS, a system that efficiently migrates the client-side of web applications across physical machines, and ReJS, a time-travel debugger for the browser.
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
> The [MS-DOS Collection](https://archive.org/details/softwarelibrary_msdos_games/v2) at the [Internet Archive](https://archive.org/) relies on [Doppio's file system](https://github.com/jvilk/browserfs) to make a large collection of DOS games playable in the browser. I worked with archive employees to integrate the file system appropriately, and to address a complex Cross-origin Resource Sharing (CORS) issue that prevented the initial deployment from working in Internet Explorer and Safari.
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
  * *Mentors*: [James Mickens](http://research.microsoft.com/en-us/people/mickens/) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
* **Research Intern**, Microsoft Research, Summer 2014.
  * *Mentors*: [James Mickens](http://research.microsoft.com/en-us/people/mickens/) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
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

* **Facebook Fellowship** for the 2015-2016 and 2016-2017 academic years, February 2015.
* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [Doppio](http://dl.acm.org/citation.cfm?id=2594293), November 2014.
* **USENIX Travel Grant Recipient**, OSDI 2014.
* **Distinguished Artifact Award** for [Doppio: Breaking the Browser Language Barrier](http://github.com/plasma-umass/doppio), PLDI 2014.
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
