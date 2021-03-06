---
title: 'RubyConf 2007, Day 2: Tightening the Feedback Loop'
date: 2007-11-03 00:00:00 Z
layout: post
---

I missed the sessions after lunch due to a soul food stupor. I regret nothing. Currently up: Phil Hagelberg on “tightening the feedback loop,” pragmatic strategies for integrating testing into the development cycle.

Hagelberg begins with a run-through of available Ruby testing tools, including Test::Unit, RSpec, and autotest. A quick poll of the room suggests that a vast majority are using some sort of test automation.

Still, Hagelberg suggests that autotest can be cumbersome and requires too much switching between the editor and terminal. He offers Flymake - which shows compiler warnings in-editor - as an intermediate improvement. A screenshot of a personal experiment with an improved visualization strategy is shown.

Then, a discussion of the [feedback principle]() that feedback is the output of a system is being fed back into the system’s input. This raises questions of what to measure, how to measure it, and when to feed the output back into the system.

Measuring the accuracy of feedback involves identifying a metric you care about, automating the measurement of that metric, and bringing notification of changes to the developer. Of course, one has to measure “meta-accuracy”, ensuring your testing system itself is reliable and trustworthy. Tools like heckle and rcov can provide a baseline of sanity for your test coverage.

Testing the human-percieved maintainability of one’s code is another challenge. While flog can offer some help, Hagelberg also suggests being judicious about a focused, clear commit strategy.

Measuring performance in an automated way is worth doing. While using a profiler is a very manual process, you can measure “black-box” response times in automated way, for example with a script that makes requests against your application. The results of these performance measurements should be visible and readily available. Keeping a history of feedback data is suggested.

Hagelberg has a tool called [Augment](http://augment.rubyforge.org/) that he then demos. Augment can ANSII-color files to show errors and failures in yellow and red respectively. Output is stored as JSON (for multi-language interchange) in an augment/ directory in your project. There’s also an Emacs helper to bring the colorized output into the editor.
