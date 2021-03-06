---
title: Emerging Programming Languages
date: 2008-12-01 00:00:00 Z
layout: post
---

This was originally an email to a private mailing list, but it seemed like it would be of interest to regular readers. Below are several interesting languages that have popped up on my radar.

[Ioke](http://kenai.com/projects/ioke/)
---------------------------------------

An experimental language by Ola Bini, one of the principal committers to the JRuby Java Virtual Machine (JVM) port of Ruby. Ioke borrows heavily from Steve Dekorte’s [Io](http://iolanguage.com), as one might guess from the name. The author’s goal seems to be an exploration of syntax and abstractions for high-level programming; performance is not a priority, according to his [blog posts](http://olabini.com/blog/tag/ioke/) on the language.

[Ur](http://www.impredicative.com/ur/)
--------------------------------------

“[M]eant to be the ultimate host for embedded domain-specific languages” according to author [Adam Chlipala](http://adam.chlipala.net/), a PhD in CompSci from Berkeley and a big fan of strict, provably correct, strongly-typed languages. Ur is a pure functional language in that vein, and it appears to be the technical foundation of a startup that the author is involved in. Examples suggest that Ur allows for XML literals, as the [Scala language](http://scala-language.org) does. The feeling of the language seems closer to Ocaml than anything else.

[AmbientTalk](http://prog.vub.ac.be/amop/at/introduction)
---------------------------------------------------------

“[A] distributed programming language developed specifically for writing programs to be deployed on mobile ad hoc networks”. If you can get past the buzzwords, you’ll find that AmbientTalk is a research language built on the JVM. The language is dynamic, prototype-based, and uses an Actor model to manage concurrency - so, very much like Io. Despite reading up on the language, it remains unclear to me what benefits it offers for network programming that aren’t available in Io, Scala, and other Actor-centric languages.

[Cobra](http://cobra-language.com/)
-----------------------------------

Quite a nice if unambitious object-oriented language with baked-in support for software contracts (remember those?). It supports both static and dynamic binding, like Objective-C, and is built on .NET (and so runs on Mono as well). With a bit of love, Cobra could be a superb general-purpose language for the .NET environment. Its clean, practically punctuation-free syntax is reminiscent of Python.

Hope at least one of those sparks the interest of the other language geeks out there. Enjoy!
