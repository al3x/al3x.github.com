---
title: Yet More on Cocoa Development with Ruby
date: 2007-10-04 00:00:00 Z
layout: post
---

Just after the Mac development love fest that was C4-[1], my interest in writing a Cocoa application was piqued. Not being an Objective-C developer (nor having any real incentive to become one), I looked around at the alternatives and saw two different options for Cocoa development with Ruby: RubyCocoa and RubyObjC. After picking the brain of [Tim Burks](http://www.neontology.com/), documenter of RubyCocoa and author of RubyObjC, I was more confused than ever about how to proceed.

Tim has since released a language called [Nu](http://programming.nu/), designed exclusively to build on and bridge with Objective-C. As part of his rationale for the new language Tim [outlined the problems inherent in bridging Ruby and Objective-C](http://programming.nu/rubycocoa-and-rubyobjc). Phrases like “overlapping”, “inconsistent”, and “incompatible” litter the document. ’Nuff said.

Nu looks neat. I built it up from source, ran the demos, and poked at the shell. It’s got a good vibe to it. But the problem for me arises in the FAQ, in response to the hypothetical, ‘Can I use Nu without knowing Objective-C?’:

> “No, at least not if you intend to use it to write Cocoa applications. In my experience, it is a mistake to think that you can use Cocoa from any higher-level language if you dont understand whats happening at the Objective-C level.”

So in order to really use Nu I need to learn Objective-C, Lisp, and Nu itself. All things I’d like to know… except, uh, Objective-C, which I was looking for an alternative to in the first place.

I understand the challenges in using a language bridge without understanding the languages on each side of that bridge. I suppose that redefines what I’m looking for: not a bridge that lets me interact with a toolkit like Cocoa, but a toolkit that supports multiple languages without having to build them from the ground up.
