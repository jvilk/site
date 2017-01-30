---
layout: page
title: About Me
image:
  feature: me-2.jpg
excerpt: "John Vilk is a sixth year PhD student at UMass Amherst."
modified: 2016-08-18T16:18:38.564948-04:00
---

I am a sixth year PhD student at the University of Massachusetts Amherst. I work in the [PLASMA](http://www.cs.umass.edu/~plasma/) lab with [Emery Berger](http://emeryberger.com/). Feel free to [contact me](../contact/) if you want to get in touch!

* Table of Contents
{:toc}

# Research

My research aims to improve the browser as an application platform by making it easier to write, debug, and optimize complex web applications.
To that end, my research interests include debugging, software performance, operating systems, and programming languages.

> **A Gray Box Approach For High-Fidelity High-Speed Time-Travel Debugging**
>
> ***John Vilk**, James Mickens, and Mark Marron*
>{: .authorlist}
>
> Time-travel debugging (TTD) lets developers step backward as well as forward through a program’s execution. TTD is a powerful mechanism for diagnosing bugs, but previous approaches suffer from poor performance due to checkpoint and logging overhead, or poor fidelity because important information like GUI state is not tracked.
>
>In this paper, we describe how to provide high-performance and high-fidelity TTD to programs written in managed languages. Previous high-performance debuggers treat components external to the program like the GUI as black boxes, but that is not sufficient for high-fidelity time-travel. Instead, we advocate for a gray-box approach that keeps these components live and in sync with the program during time-travel. The key insight is that managed runtime APIs expose most of the functionality required to do this; where it does not, we extend the runtime with a small number of non-intrusive interrogative interfaces. To demonstrate the power of our gray-box approach, we implement ReJS, a time-traveling debugger for web applications. ReJS imposes imperceptible tracing overhead, and its logs typically grow less than 1 KB/s. As a result, ReJS is performant enough to be deployed in the wild; real client machines can ship buggy execution traces across the wide area to developer-side machines for debugging.
>
> This work is currently in submission.
>
> * [Tech Report](https://www.microsoft.com/en-us/research/publication/gray-box-approach-high-fidelity-high-speed-time-travel-debugging/)
> * [Source Code (Core of Debugger)](https://github.com/Microsoft/ChakraCore/tree/TimeTravelDebugging)
> * [MSDN Channel 9 Coverage: Demo of early version (Video)](https://channel9.msdn.com/blogs/Marron/Time-Travel-Debugging-for-JavaScriptHTML)
>{: .hlist}
{: .project}

> **Browsix: Bridging the Gap Between Unix and the Browser**
>
> *Bobby Powers, **John Vilk**, and Emery D. Berger*
>{: .authorlist}
>
> Applications written to run on conventional operating systems typically depend on OS abstractions like processes, pipes, signals, sockets, and a shared file system. Porting these applications to the web currently requires extensive rewriting or hosting significant portions of code server-side because browsers present a nontraditional runtime environment that lacks OS functionality.
>
> This paper presents Browsix, a framework that bridges the considerable gap between conventional operating systems and the browser, enabling unmodified programs expecting a Unix-like environment to run directly in the browser. Browsix comprises two core parts: (1) a JavaScript-only system that makes core Unix features (including pipes, concurrent processes, signals, sockets, and a shared file system) available to web applications; and (2) extended JavaScript runtimes for C, C++, Go, and Node.js that support running programs written in these languages as processes in the browser. Browsix supports running a POSIX shell, making it straightforward to connect applications together via pipes.
>
> We illustrate Browsix's capabilities via case studies that demonstrate how it eases porting legacy applications to the browser and enables new functionality. We demonstrate a Browsix-enabled LaTeX editor that operates by executing unmodified versions of pdfLaTeX and BibTeX. This browser-only LaTeX editor can render documents in seconds, making it fast enough to be practical. We further demonstrate how Browsix lets us port a client-server application to run entirely in the browser for disconnected operation. Creating these applications required less than 50 lines of glue code and no code modifications, demonstrating how easily Browsix can be used to build sophisticated web applications from existing parts without modification.
>
> This work was recently accepted to ASPLOS 2017.
>
> * [ASPLOS '17 Preprint](https://arxiv.org/abs/1611.07862)
> * [Webpage](https://browsix.org/)
> * [Source Code](https://github.com/plasma-umass/browsix)
>{: .hlist}
{: .project}

> **SurroundWeb: Mitigating Privacy Concerns in a 3D Web Browser**
>
> ***John Vilk**, David Molnar, Eyal Ofek, Chris Rossbach, Benjamin Livshits, Alexander Moshchuk, Helen J. Wang, and Ran Gal*
>{: .authorlist}
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
> * [IEEE S&P '15 Presentation (Video)](https://www.youtube.com/watch?v=BO3rQ9R5gKM)
> * [TechFair 2014 (Video)](http://research.microsoft.com/apps/video/?id=212669)
> * [BBC Coverage (Video)](http://www.bbc.com/news/technology-27243375)
> {: .hlist}
{: .project}

> **Doppio: Breaking the Browser Language Barrier**
>
> ***John Vilk** and Emery D. Berger*
>{: .authorlist}
>
> Doppio is a JavaScript-based runtime system that makes it possible to run unaltered applications written in general-purpose languages directly inside the browser. Doppio provides a wide range of runtime services, including a file system that enables local and external (cloud-based) storage, an unmanaged heap, sockets, blocking I/O, and multiple threads. We demonstrate Doppio's usefulness with two case studies: we extend Emscripten with Doppio, letting it run an unmodified C++ application in the browser with full functionality, and present DoppioJVM, an interpreter that runs unmodified JVM programs directly in the browser. This work appeared at [PLDI 2014](http://conferences.inf.ed.ac.uk/pldi2014/), won the [Distinguished Artifact Award](http://pldi14-aec.cs.brown.edu/), and was selected as a [SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)!
>
> DoppioJVM is currently used by the University of Illinois at [CodeMoo.com](http://codemoo.com/) to teach children how to program in Java, and components of Doppio are used by the [MS-DOS Collection](https://archive.org/details/softwarelibrary_msdos_games/v2) at the [Internet Archive](https://archive.org/).
>
> * [Demo](http://doppiojvm.org/)
> * [Source Code](https://github.com/plasma-umass/doppio)
> * [PLDI '14 Paper](http://dl.acm.org/citation.cfm?id=2594293) ([Alt. Link](https://plasma-umass.github.io/doppio-demo/paper.pdf))
> * [Talk @ Microsoft Research (Video)](https://www.youtube.com/watch?v=i1JzZIq82uU)
> {: .hlist}
{: .project}

# Side Projects

Occasionally, I find the time to work on some fun side projects.

> **MakeTypes: TypeScript Types from JSON Examples**
>
> MakeTypes lets developers typecheck code that interacts with JSON services
> by generating TypeScript types from JSON examples. MakeTypes can also optionally
> perform *runtime type checking* to enforce these types at runtime, guarding code
> against unexpected service responses.
>
> MakeTypes uses the Common Preferred Shape Relation from [this PLDI paper](https://dl.acm.org/citation.cfm?id=2908115).
>
> * [Demo](https://jvilk.com/MakeTypes)
> * [NPM Module](https://www.npmjs.com/package/maketypes)
> * [Source Code](https://github.com/jvilk/maketypes)
> {: .hlist}
{: .project}

> **TypeScript Generator for Dropbox's Stone**
>
> Stone is a language-agnostic specification language for APIs. Stone's generators can generate
> SDKs for a variety of languages from a Stone specification, including JavaScript.
>
> I mapped [Stone's types onto TypeScript's type system](https://github.com/dropbox/stone/pull/14),
> and implemented a Stone generator that produces TypeScript definition files for its JavaScript
> generator.
>
> This generator will [eventually provide TypeScript types for the Dropbox JavaScript SDK.](https://github.com/dropbox/dropbox-sdk-js/pull/96)
>
> * [Source Code](https://github.com/dropbox/stone)
> * [Mapping from Stone's types to TypeScript's type system](https://github.com/dropbox/stone/pull/14)
> {: .hlist}
{: .project}

> **MS-DOS Collection at the Internet Archive**
>
> The [MS-DOS Collection](https://archive.org/details/softwarelibrary_msdos_games/v2) at the [Internet Archive](https://archive.org/) relies on [Doppio's file system](https://github.com/jvilk/browserfs) to make a large collection of DOS games playable in the browser.
> I added support for [union mounting](https://en.wikipedia.org/wiki/Union_mount) into the file system to support layering a mutable file system on top of an immutable zip file,
> making it possible to save game progress to in-browser storage.
> I also worked with archive employees to integrate the file system appropriately, and to address a complex Cross-origin Resource Sharing (CORS) issue that prevented the initial deployment from working in Internet Explorer and Safari.
>
> * [Homepage](https://archive.org/details/softwarelibrary_msdos_games/v2)
> * [Blog Post on Game Saving](http://ascii.textfiles.com/archives/4924)
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

# Experience

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

# Education

* **Ph.D. in Computer Science**, University of Massachusetts, In Progress.
* **M.S. in Computer Science**, University of Massachusetts, 2014.
* **B.S. in Computer Science**, Worcester Polytechnic Institute, 2011.
{: .simplelist}

# Awards

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

# Professional Activities

* **External Review Committee Member**, PLDI 2017.
* **External Review Committee Member**, PLDI 2016.
* **Mentor**, [Computing Beyond the Double Bind Mentoring Network](https://www.terc.edu/display/Projects/Computing+Beyond+the+Double+Bind%3A+Women+of+Color+in+Computing+Education+and+Careers), 2015-2016.
  * As a part of this program, I remotely mentor two undergraduate women of color to provide them with a listening ear and professional guidance.
* **Member**, IEEE, 2015-present.
* **Member**, USENIX, 2014-present.
* **Graduate Representative**, academic year 2014-2015, University of Massachusetts School of Computer Science.
  * Graduate representatives attend and vote during faculty meetings, meet and provide feedback on faculty candidates, and form a bridge between the graduate students and the faculty as a whole.
* **Student Volunteer**, PLDI 2016, PLDI 2016 PC Meeting, OOPSLA 2014.
* **Artifact Evaluation Committee Member**: OOPSLA 2015, PLDI 2015, OOPSLA 2014.
* **External Reviewer:** USENIX Security 2014, PLDI 2014, OOPSLA 2012, MSPC 2012, HotPar 2012.
* **Member**, ACM, 2008-present.
{: .simplelist}

# Teaching

* **Guest Lecturer**, COMPSCI 326: Web Development, University of Massachusetts Amherst, Spring 2016.
* **T.A.**, COMPSCI 326: Web Development, University of Massachusetts Amherst, Spring 2016.
  * For a class of 100 undergraduates, I developed the curriculum, designed and wrote all of the assignments, graded most assignments, held office hours, and answered hundreds of questions on Piazza.
* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2015.
  * *Students*: Muhammad Bhatti
* **Mentor**, Doppio, PLASMA Lab, Google Summer of Code, Summer 2013.
  * *Students*: [Giles Lavelle](http://lavelle.co/) & Braden McDorman
{: .simplelist}
