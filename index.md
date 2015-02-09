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

> **SurroundWeb: Mitigating Privacy Concerns in a 3D Web Browser**
>
> Immersive experiences that mix digital and real-world objects are becoming reality, but they raise serious privacy concerns as they require real-time sensor input. SurroundWeb is the first 3D web browser that provides the novel functionality of rendering web content onto a room while tackling many of the inherent privacy challenges. Following the principle of least privilege, we propose three abstractions for immersive rendering:
>
> 1. The *room skeleton* lets applications place content in response to the physical dimensions and locations of renderable surfaces in a room.
> 2. The *detection sandbox* lets applications declaratively place content near recognized objects in the room without revealing if the object is present.
> 3. *Satellite screens* let applications display content across devices registered with SurroundWeb.
>
> We implement these abstractions in a prototype system, an demonstrate that a wide range of immersive experiences can be implemented  with acceptable performance. SurroundWeb will appear at [IEEE Security and Privacy 2015](http://www.ieee-security.org/TC/SP2015/).
>
> * IEEE S&P '15 Paper (Coming soon!)
> * [Tech Report](http://research.microsoft.com/apps/pubs/?id=209968)
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

* **Research Intern**, Microsoft Research, Summer 2014.
* **Research Intern**, Microsoft Research, Summer 2013.
* **Software Engineering Intern**, Google, Summer 2012.
* **Research Assistant**, University of Massachusetts, 2011 to present.
* **Research Intern**, MIT Lincoln Laboratory, Summer 2011.
* **Software Engineering Intern**, SoftArtisans Inc., Summer 2010.
{: .simplelist}

## Awards

* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [Doppio](http://dl.acm.org/citation.cfm?id=2594293), November 2014.
* **Distinguished Artifact Award** for [DoppioJVM](http://github.com/plasma-umass/doppio), PLDI 2014.
{: .simplelist}

## Teaching

* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2013.
{: .simplelist}

## Education

* **M.S. in Computer Science**, University of Massachusetts, 2014.
* **B.S. in Computer Science**, Worcester Polytechnic Institute, 2011.
{: .simplelist}
