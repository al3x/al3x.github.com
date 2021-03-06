---
title: 'RubyConf 2007, Day 2: Mac OS X Loves Ruby'
date: 2007-11-03 00:00:00 Z
layout: post
---

Apple’s latest release of Mac OS X brings with it a number of improvements to and integrations with Ruby. Speaker Laurent Sansonetti - “Ruby Ninja” on his introductory slide - is the man behind much of this work. I’m amped for this talk.

Fundamentally, the distribution of Ruby in Leopard is much improved. It allows for multiple versions of Ruby to be present on the system, each with its own suite of gems. The version of Ruby shipped has support for DTrace, and Ruby has been integrated into Xcode and Interface Builder.

RubyCocoa, a bridge to Cocoa and C APIs, is included and supported by Apple in Leopard. Two RubyCocoa applications, PackRat and LimeChat, are offered as examples of robust applications taking advantage of the bridge. Leopard Server’s own Podcast Producer makes use of Rails and RubyCocoa.

RubyCocoa works by creating proxies that forward messages from the Ruby runtime to its target Cocoa/C runtime. RubyCocoa can forward exceptions, convert types, and maintains Objective-C objects for the programmer. The bridge will also manage garbage collection. The messaging convention is to substitute every “.” with an underscore in the method name (selector), while optionally omitting the final underscore.

Demos
-----

Laurent then demos the creation of a simple RubyCocoa application. He creates a simple window in Interface Builder, containing a text input box and a button labeled “Speech!”. Over in Xcode, he whips up some Ruby (complete with decent syntax highlighting). Interface Builder is aware of Ruby classes, outlets, and actions in the file he’s editing back in Xcode. Predictably, the application reads aloud whatever in typed into the input box after hitting the button. It works! Applause.

Laurent then demos CocoaRepl, which allows for real-time evaluation of Ruby code. Window creation, Quartz Composer loading, and Ruby threads. The audience groans with geek lust as a window containing a Quartz composition is scaled while its opacity is modified, all code being executed from CocoaRepl.

A final demo: inject.rb, which allows a Ruby interpreter to be injected into the process context of a running Cocoa application. Laurent messes around with an instance of TextEdit from irb, grabbing properties about the window, changing the window’s title and contents. More applause. Then, an instance of TextEdit whose input area is, itself, turned into an instance of irb. Fun.

Objective-C’s APIs are described as “introspectible”, while standard C APIs are a bit more difficult to interact with. Apple’s new BridgeSupport provides XML metadata that covers static APIs, as well as a metadata generator so developers can allow bridges to take advantage of their own APIs. BridgeSupport is being used in both Ruby and PyObjC, as well as in Xcode, which is using it for auto-completion. Laurent demos BridgeSupport by generating metadata for libpcap and then using the resulting bridge output to write a basic sniffer in Ruby.

Running low on time, Laurent runs through an overview of the DTrace support in Leopard’s Ruby. Probes in Ruby are available for function entry and return, exceptions, garbage collection, object creation and destruction, and more. A simple script is shown that will print function entries and returns, and said script is demoed. Leopard provides a graphical interface to DTrace’s programmable probes called Instruments, and this is demoed tracing through an instance of LimeChat.

Wrapping up, Laurent talks about some of the limitations of bridging, including caching of instances, maintaining the object model twice, and converting objects and exceptions. Presently, RubyCocoa can’t use Objective-C 2.0’s garbage collection. Ruby 1.8 is also not thread safe, which presents some problems (this will be alleviated in Ruby 1.9). Laurent suggests that his team’s future goal is to write the Ruby class model on top of the Objective-C runtime, which would solve many of the problems listed above.

Questions:
----------

Can you distribute RubyCocoa apps on OS X versions earlier than Leopard? Yes, apparently there’s a script for that.

Possible to see this on the iPhone? Next question. Big laughs.

Is the downloadable version the same as what’s in Leopard? Not quite, but it’s coming soon.

Building with a Rakefile rather than Xcode? You lose support, but you can try rucola as an alternative.

Do you lose Objective-C semantics in the conversion process? It’s a work in progress.

Gem packaging? standaloneify is a work in progress.

Will the GC in Objective-C be committed to GCC? It’s a different piece…

Keeping things up to date? You can do a gem update, but only big bugs and security problems will be addressed in Ruby itself. Not going to overwrite 1.8 with 1.9. Shooting for compatibility.

Why RubyCocoa over RubyObjC (my question)? RubyObjC was too small a project, wrong license, not the right features, etc.
