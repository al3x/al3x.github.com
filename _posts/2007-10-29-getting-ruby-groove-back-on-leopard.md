---
title: Getting Ruby's Groove Back on Leopard
date: 2007-10-29 00:00:00 Z
layout: post
---

Apple has [done good](http://trac.macosforge.org/projects/ruby/wiki/WhatsNewInLeopard) with the version of Ruby that ships with Leopard. It’s got readline, it’s got DTrace probes, it’s got gem, it’s got a sane default collection of gems, and by god, they actually seem to have integrated it with Xcode and Interface Builder. Oh, and it’s cross-platform for 32- and 64-bit. Yeah. What.

With all that in mind, I clearly want to use Apple’s pimped out Ruby even though my MacPorts version (installed while in Tiger) seems to work fine. So, some experiments.

1.  If you install the very latest MySQL (the fancy Mac installer one), you can actually bulid the mysql gem with only [a minor incantation](http://trac.macosforge.org/projects/ruby/wiki/Troubleshooting). Much improved from Tiger, on which I had basically given up hope of ever having a working MySQL gem.
2.  Just for shits, let’s ditch MacPorts entirely because it sucks and I use it for less and less as time goes on. Take /opt/local/bin out of your shell’s PATH. Now let’s install everything I need for daily Ruby coding. Whoa. That basically all works. Everything except… rmagick. Oh. Crap.
3.  Attempt to install the necessary dependency libraries for ImageMagick by hand. FAIL. Some crazy Freetype/Ghostscript font issue, not to mention that you get bizarre errors if you make clean install and re-configure in the ImageMagick source directory. Life’s too short for this bull.
4.  Throw out old, crap-landen MacPorts install with a sudo rm -rf /opt. Reinstall MacPorts, selfupdate.
5.  [Follow these instructions to get a working rmagick gem](http://nullstyle.com/2007/10/27/how-to-build-imagemagick-and-install-rmagick-with-macports-on-mac-os-x-leopard/). Note the comments. Basically, all MacPorts is doing is taking care of the miserable chain of suffering that ImageMagick necessitates. I don’t trust it with much else. (Well, save sudo port install git +svn, but it stings just a little. Ow, my pride.)

Now I’ve got Apple’s tricked-out Ruby ready to do my day-to-day work. Sweet. Next experiments: seeing how well they’ve really integrated Ruby into the Cocoa development process, and messing with DTrace instruments.
