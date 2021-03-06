---
layout: page
title: About Me
image:
  feature: me-2.jpg
excerpt: "John Vilk is PhD candidate at UMass Amherst."
modified: 2018-11-18T16:18:38.564948-04:00
---

I am a software engineer at [Stripe](https://stripe.com/) working remotely from Corvallis, Oregon. Prior to that, I completed my PhD at the University of Massachusetts Amherst while working in the [PLASMA](http://www.cs.umass.edu/~plasma/) lab with [Emery Berger](http://emeryberger.com/). Feel free to [contact me](../contact/) if you want to get in touch!

* Table of Contents
{:toc}

# Research

My research spans software systems, programming languages, and software engineering, with a focus on overcoming challenges posed by web application development.
My research interests include, but are not limited to, software debugging, performance, portability, and reliability.

> **Comedians in cafes getting data: Evaluating timing and adaptivity in real-world robot comedy performance**
>
> ***John Vilk** and Naomi T. Fitter*
>{: .authorlist}
>
>Social robots and autonomous social agents are becoming more ingrained in our everyday lives. Interactive agents from Siri to Anki's Cozmo robot include the ability to tell jokes to engage users. This ability will build in importance as in-home social agents take on more intimate roles, so it is important to gain a greater understanding of how robots can best use humor. Stand-up comedy provides a naturally-structured experimental context for initial studies of robot humor. In this preliminary work, we aimed to compare audience responses to a robotic stand-up comedian over multiple performances that varied robot timing and adaptivity. Our first study of 22 performances in the wild showed that a robot with good timing was significantly funnier. A second study of 10 performances found that an adaptive performance was not necessarily funnier, although adaptations almost always improved audience perception of individual jokes. The end result of this research provides key clues for how social robots can best engage people with humor.
>
> This work was awarded a Best Paper Award at HRI 2020.
>
> * [HRI '20 Paper](https://dl.acm.org/doi/10.1145/3319502.3374780) [(Alt. link)](https://drive.google.com/file/d/1rXlc3QDOl-NAu0fSvjITISdbGbwstOok/view?usp=sharing)
> * [HRI '20 Presentation (Video)](https://www.youtube.com/watch?v=to2FQRYrbXQ)
>{: .hlist}
{: .project}

> **Righting Web Development**
>
> ***John Vilk***
>{: .authorlist}
>
> This dissertation revisits web development and provides developers with a complete set of development tools with full support for the browser environment. McFly is the first time-traveling debugger for the browser, and lets developers debug web applications and their visual state during time-travel; components of this work shipped in Microsoft's ChakraCore JavaScript engine. BLeak is the first system for automatically debugging memory leaks in web applications, and provides developers with a ranked list of memory leaks along with the source code responsible for them. BCause constructs a causal graph of a web application's events, which helps developers understand their code's behavior. Doppio lets developers run code written in conventional languages in the browser, and Browsix brings Unix into the browser to enable unmodified programs expecting a Unix-like environment to run directly in the browser. Together, these five systems form a solid foundation for web development.
>
> My dissertation was chosen as an [*Outstanding Doctoral Dissertation*](https://www.cics.umass.edu/news/seven-graduate-students-receive-cics-outstanding-graduate-awards) by the UMass Amherst College of Information and Computer Sciences.
>
> * [PhD Dissertation](https://scholarworks.umass.edu/dissertations_2/1405/)
> * [Dissertation Defense (Video)](https://www.youtube.com/watch?v=H0sovocOlNg)
>{: .hlist}
{: .project}

> **ReJS: Time-Travel Debugging for Browser-Based Applications**
>
> ***John Vilk**, Emery D. Berger, James Mickens, and Mark Marron*
>{: .authorlist}
>
> Time-traveling debuggers offer the promise of simplifying debugging by letting developers freely step forwards and backwards through a program's execution. However, web applications present multiple challenges that make time-travel debugging especially difficult. A time-traveling debugger for web applications must accurately reproduce all network interactions, asynchronous events, and visual states observed during the original execution, both while stepping forwards and backwards. This must all be done in the context of a complex and highly multithreaded browser runtime. At the same time, to be practical, a time-traveling debugger must maintain interactive speeds.
>
> This paper presents McFly, the first time-traveling debugger for web applications. McFly departs from previous approaches by operating on a high-level representation of the browser's internal state. This approach lets McFly provide accurate time-travel debugging - maintaining JavaScript and visual state in sync at all times - at interactive speeds. McFly's architecture is browser-agnostic, building on web standards supported by all major browsers. We have implemented McFly as an extension to the Microsoft Edge web browser, and core parts of McFly have been integrated into a time-traveling debugger product from Microsoft.
>
> * [Arxiv Paper](https://arxiv.org/abs/1810.11865)
> * [ChakraCore Source Code](https://github.com/Microsoft/ChakraCore)
> * [MSDN Channel 9 Coverage: Demo of alpha (Video)](https://channel9.msdn.com/blogs/Marron/Time-Travel-Debugging-for-JavaScriptHTML)
>{: .hlist}
{: .project}

> **BLeak: Automatically Debugging Memory Leaks in Web Applications**
>
> ***John Vilk** and Emery D. Berger*
>{: .authorlist}
>
>Despite the presence of garbage collection in managed languages like JavaScript, memory leaks remain a serious problem. In the context of web applications, these leaks are especially pervasive and difficult to debug.  Web application memory leaks can take many forms, including failing to dispose of unneeded event listeners, repeatedly injecting iframes and CSS files, and failing to call cleanup routines in third-party libraries. Leaks degrade responsiveness by increasing GC frequency and overhead, and can even lead to browser tab crashes by exhausting available memory. Because previous leak detection approaches designed for conventional C, C++ or Java applications are ineffective in the browser environment, tracking down leaks currently requires intensive manual effort by web developers.
>
> This paper introduces BLeak (**B**rowser **Leak** debugger), the first system for automatically debugging memory leaks
> in web applications. BLeak's algorithms leverage the observation that in modern web applications, users often repeatedly return to the same (approximate) visual state (e.g., the inbox view in Gmail). Sustained growth between round trips is a strong indicator of a memory leak. To use BLeak, a developer writes a short script (≈40 LOC) to drive a web application in round trips to the same visual state. BLeak then automatically generates a list of leaks found along with their root causes, ranked by severity. Guided by BLeak, we identify and fix over 50 memory leaks in popular libraries and apps including Airbnb, AngularJS, Google Analytics, Google Maps SDK, and jQuery. BLeak's median precision is 100%; fixing the leaks it identifies reduces heap growth by an average of 94%, saving from 0.5 MB to 8 MB per round trip.
>
> BLeak appeared at PLDI 2018 and was selected as a [SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/).
>
> * [Website](http://bleak-detector.org/)
> * [PLDI '18 Paper](https://dl.acm.org/citation.cfm?id=3192366.3192376) [(Alt. link)](https://jvilk.com/assets/pdf/bleak.pdf)
> * [PLDI '18 Presentation (Video)](https://www.youtube.com/watch?v=RzofyIvaY6A)
> * [Source Code](https://github.com/plasma-umass/bleak)
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
> This work appeared at ASPLOS 2017.
>
> * [ASPLOS '17 Paper](https://dl.acm.org/citation.cfm?id=3037727) [(Alt. link)](https://jvilk.com/assets/pdf/asplos17.pdf)
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
> We implement these abstractions in a prototype system, and demonstrate that a wide range of immersive experiences can be implemented  with acceptable performance.
>
> SurroundWeb appeared at [IEEE S&P 2015.](http://www.ieee-security.org/TC/SP2015/)
>
> * [IEEE S&P '15 Paper](http://ieeexplore.ieee.org/document/7163040/) [(Alt. link)](https://jvilk.com/assets/pdf/oakland15.pdf)
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
> DoppioJVM is currently used by the University of Illinois at [CodeMoo.com](http://codemoo.com/) to teach students how to program in Java, and Doppio is used by the [Software Collection](https://archive.org/details/software) at the [Internet Archive](https://archive.org/) to bring historical software to life in the browser.
>
> * [PLDI '14 Paper](http://dl.acm.org/citation.cfm?id=2594293) ([Alt. Link](https://plasma-umass.github.io/doppio-demo/paper.pdf))
> * [Demo](http://doppiojvm.org/)
> * [Source Code](https://github.com/plasma-umass/doppio)
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
> MakeTypes uses the Common Preferred Shape Relation from [Petricek et al. (PLDI 2016)](https://dl.acm.org/citation.cfm?id=2908115).
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
> I mapped [Stone's type system onto TypeScript's type system](https://github.com/dropbox/stone/pull/14),
> and implemented a Stone generator that produces TypeScript definition files from a Stone API
> specification.
>
> This generator provides TypeScript types for the [Dropbox JavaScript SDK](https://github.com/dropbox/dropbox-sdk-js).
>
> * [Source Code](https://github.com/dropbox/stone)
> * [Mapping from Stone's type system to TypeScript's type system](https://github.com/dropbox/stone/pull/14)
> {: .hlist}
{: .project}

> **Software Collection at the Internet Archive**
>
> The [Software Collection](https://archive.org/details/software) at the [Internet Archive](https://archive.org/) relies on [Doppio's file system](https://github.com/jvilk/browserfs) to make a large collection of software playable in the browser.
> I added support for [union mounting](https://en.wikipedia.org/wiki/Union_mount) into the file system to support layering a mutable file system on top of an immutable zip file,
> making it possible to load software from a zip file and persist file system changes to in-browser storage.
>
> * [Homepage](https://archive.org/details/softwarelibrary_msdos_games/v2)
> * [Blog Post on Game Saving](http://ascii.textfiles.com/archives/4924)
> {: .hlist}
{: .project}

> **JSMESS: Multi Emulator Super System in JavaScript**
>
> The [JSMESS](http://jsmess.textfiles.com/) project aims to port the [Multi Emulator Super System (MESS)](http://mess.org/) to JavaScript to enable accurate and embeddable vintage computer and video game console emulators in the browser. This project has enabled the [Internet Archive](http://archive.org/) to provide its visitors with interactive demos of vintage and historical software for educational purposes. JSMESS uses [Emscripten](https://github.com/kripken/emscripten) along with tweaks to the MESS source code to accomplish this feat.
>
> JSMESS is now officially part of MESS/MAME.
>
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

# Education

* **Ph.D. in Computer Science**, University of Massachusetts, Anticipated September, 2018.
  * *Advised by* [Emery D. Berger.](https://emeryberger.com/)
* **M.S. in Computer Science**, University of Massachusetts, 2014.
* **B.S. in Computer Science**, Worcester Polytechnic Institute, May, 2011.
{: .simplelist}

# Employment

* **Software Engineer**, Stripe, 2018 to present.
* **Research Assistant**, University of Massachusetts, 2011 to 2018.
  * *With the* [PLASMA](https://plasma.cs.umass.edu/) *group, working with* [Emery D. Berger.](https://emeryberger.com/)
* **Teaching Assistant**, University of Massachusetts, Spring 2016.
  * *For CMPSCI 326: Web Programming, with* [Professor Timothy Richards](https://tim-umass.github.io/).
* **Research Intern**, Microsoft Research, Summer 2015.
  * *Mentors*: [James Mickens](http://www.seas.harvard.edu/directory/mickens) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
* **Research Intern**, Microsoft Research, Summer 2014.
  * *Mentors*: [James Mickens](http://www.seas.harvard.edu/directory/mickens) and [Mark Marron](http://research.microsoft.com/en-us/um/people/marron/)
* **Research Intern**, Microsoft Research, Summer 2013.
  * *Mentor*: [David Molnar](http://research.microsoft.com/en-us/people/dmolnar/)
* **Software Engineering Intern**, Google, Summer 2012.
  * *With the Java Platform Team.*
* **Research Intern**, MIT Lincoln Laboratory, Summer 2011.
  * *In Division 6: Communication Systems*
* **Software Engineering Intern**, SoftArtisans Inc., Summer 2010.
{: .simplelist}

# Honors & Awards

* **Best Paper Award** for [Comedians in cafes getting data: Evaluating timing and adaptivity in real-world robot comedy performance](https://dl.acm.org/doi/10.1145/3319502.3374780), HRI 2020.
* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [BLeak: Automatically Debugging Memory Leaks in Web Applications](https://dl.acm.org/citation.cfm?id=3192366.3192376), 2019.
* **[Outstanding Doctoral Dissertation Award](https://www.cics.umass.edu/news/seven-graduate-students-receive-cics-outstanding-graduate-awards)** from the UMass Amherst College of Information and Computer Sciences, 2019.
* **Facebook Ph.D. Fellowship** in Programming Languages and Compilers, 2015-2017.
* **[SIGPLAN Research Highlight](http://www.sigplan.org/Newsletters/CACM/Papers/)** for [Doppio: Breaking the Browser Language Barrier](http://dl.acm.org/citation.cfm?id=2594293), 2014.
* **Distinguished Artifact Award** for [Doppio: Breaking the Browser Language Barrier](http://github.com/plasma-umass/doppio), PLDI 2014.
* **Inducted** into the WPI chapter of Upsilon Pi Epsilon computer science honor society, 2011.
* **Salisbury Prize**, WPI, 2011.
  * *Awarded for completing all of my requirements at WPI "faithfully, industriously, and with distinguished attainment"*.
* **Dr. Neil G. Sullivan Memorial Award**, WPI, 2010.
  * *Awarded annually to three junior undergraduates in recognition of their demonstrated ability and promise.*
* **Charles O' Thompson Scholar**, WPI, 2008.
  * *Recognizes outstanding performance by first-year undergraduate students.*
* **Travel Grants**, PLDI 2016, IEEE S&P 2015, OSDI 2014, PLDI 2014, POPL 2012.
{: .simplelist}

# Professional Service

* **Program Committee Member**, PLDI 2020.
* **External Review Committee Member**, PLDI 2016, PLDI 2017.
* **Artifact Evaluation Committee Member**, OOPSLA 2015, PLDI 2015, OOPSLA 2014.
* **Graduate Representative**, University of Massachusetts College of Information and Computer Sciences, 2014-2015.
  * *One of four Ph.D. students elected to serve for one year. Attended and voted during faculy meetings, met with faculty candidates, and organized department seminars.*
* **Student Volunteer**, PLDI 2016, PLDI 2016 PC Meeting, OOPSLA 2014.
* **External Reviewer**, USENIX Security 2014, PLDI 2014, OOPSLA 2012, MSPC 2012, HotPar 2012.
{: .simplelist}

# Teaching & Mentoring

* **Guest Lecturer**, COMPSCI 326: Web Development, University of Massachusetts Amherst, Spring 2016.
* **Teaching Assistant**, COMPSCI 326: Web Development, University of Massachusetts Amherst, Spring 2016.
  * *As a TA, I co-taught the class with the instructor. I redesigned the curriculum, designed and wrote all of the assignments, graded assignments, held well-attended office hours, and answered hundreds of questions on Piazza. An archived version of the course website and assignments can be found* [here.](https://jvilk.com/cmpsci-326)
* **Research Mentor**
  * **Muhammad Bhatti**, Undergraduate in Computer Science, [NUST](http://www.nust.edu.pk/), Pakistan, Summer 2015.
    * *Remotely supervised contributions to a research project via Google Summer of Code. Extended an [experimental Python implementation](https://github.com/plasma-umass/ninia) with multithreading support.*
  * **Giles Lavelle**, Undergraduate in Computer Science, University of Bristol, Summer 2013.
    * *Remotely supervised contributions to Doppio via Google Summer of Code. Extended Doppio's file system with cloud storage support.*
  * **Braden McDorman**, Undergraduate in Computer Science, University of Oklahoma, Summer 2013.
    * *Remotely supervised contributions to Doppio via Google Summer of Code. Extended Doppio with support for outgoing TCP sockets.*
* **Mentor**, [Computing Beyond the Double Bind Mentoring Network](https://www.terc.edu/display/Projects/Computing+Beyond+the+Double+Bind%3A+Women+of+Color+in+Computing+Education+and+Careers), 2015-2016.
  * *Provided remote guidance and support to undergraduate women of color in computer science.*
{: .simplelist}
