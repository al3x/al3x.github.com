---
title: My Get-Back-To-Work Hack
date: 2009-09-14 00:00:00 Z
layout: post
---

I’ve been looking for a way to fight distractions on the web. I’ve tried [SelfControl](http://visitsteve.com/work/selfcontrol/), but just getting a “server not found” error in the browser when I visit a temptingly unproductive site isn’t particularly motivational.

The hack for this I came up with today is cheap and dumb, but it works. If you want to be sure it’s worth your time, watch this 46 second long [screencast](http://screenr.com/Ix7), then read on if you like what you see.

If you’re an experienced web developer, this will probably take you all of ten minutes to set up. If not, I’ve tried to explain it in pretty friendly terminology, but you might want to grab the nearest techie to help you out.

Step One: Block Distracting Domains
-----------------------------------

The `/etc/hosts` file tells your computer where other computers are. Normally, this file is almost empty; it just points your computer at itself, reminding it that its local address is `127.0.0.1`. Your computer doesn’t need to know much more than that because it uses [DNS](http://en.wikipedia.org/wiki/Domain_Name_System) and similar protocols to find other computers over the network. Still, every time your computer tries to talk to another computer, it checks `/etc/hosts` to see if we’ve specified the other computer’s address.

We can make use of the `/etc/hosts` file to block specific domains that we shouldn’t be spending time on. We just associate those domains with a bad address - in this case, the address of our local machine.

My `/etc/hosts` looks like [this](http://gist.github.com/187138). It’s the lines below the commented-out line about “distractions” that matter. Those lines say that the specified domains are served by my own computer. They aren’t, of course, so when I visit those sites, my browser gives me an error page.

Go ahead and put your own time-wasting sites in there; be sure to add the “www.” variant, if the site has one. If you like, you can collapse all the domains onto one line after the “127.0.0.1”, but I find it easier to read over multiple lines.

To an extent, this solves the problem: if you visit one of the domains you added to the file, you don’t get there. But as with SelfControl’s solution, an error page in your browser isn’t very motivational. Let’s go further.

Step Two: Serving Content for Blocked Domains
---------------------------------------------

Since we’re directing requests for distracting domains to our own system, why not do something with those requests? Fire up a web server on the usual port (80). On a Mac, this is as simple as going to Sharing in System Preferences and ticking the box for Web Sharing. The text there may say that your computer’s website is available at some fancy address, but it’s also available on <http://127.0.0.1/>.

Now, visit one of those sites you put in your `/etc/hosts`. You get a real webpage this time, right? Most likely, it’s whatever default page came with your web server software; it might say “It worked!” or something equally inane. The name of this file is probably `index.html.en` (or maybe without the “.en” part). On a Mac, it lives at `/Library/WebServer/Documents/index.html.en`. You should modify that file. Make it pretty, but not too pretty. Put a message in there that’s motivational to you. Visit one of your blocked sites, and you should see your custom message instead. Pretty good.

There’s a problem, though. Say you blocked dumbsite.com. If you visit `http://dumbsite.com/foo/bar/baz.html`, you’ll get a `404 File Not Found` error from your local web server. That’s because you don’t have the files and directories the server is looking for inside the default folder your web server stores web pages in. You don’t want to have to provide these, either; you just want to serve the same page for every domain you’ve blocked.

If you’re using Apache, you can use a couple of lines like [this](http://gist.github.com/187146) inside your `httpd.conf` to rewrite any URL to point to a file in your document root (in this case, `index.php`, but change that to whatever you want). That will get you back to seeing your custom page when you visit a blocked domain, regardless of the URL.

If you want to keep it simple, get all that working and stop here. You’ve got a nice custom reminder to get back to work, and few moving parts to maintain. If you’re comfortable setting up PHP, though, venture on for a little gravy.

Step Three: Doing Something Useful with Blocked Domains
-------------------------------------------------------

I didn’t just want a motivational message. I wanted a reminder of exactly what I should be doing.

Once I got the above working, I flipped on PHP in my `httpd.conf` and set Apache to run as my user. Then, I changed my `index.php` to [this](http://gist.github.com/187147). The key lines are at the bottom. They tell PHP to fire off a command, just as if I issued it from a terminal. In my setup, the command will fire up [Things](http://culturedcode.com/things/) if it isn’t running, or move it to the front of my windows if it is.

Variations
----------

There’s a bunch of ways you could do this differently. Rather than modifying `/etc/hosts`, you could firewall off any distracting domains. You could run your own HTTP proxy and do the filtering there. Or, rather than popping up an application, you could have that PHP script (or however you decide to implement it) pull your to-do list right into the admonishing web page. Or, you could, y’know, just use plain old real actual self control. But that’s easier said than done, I’ve found.

What you do with the block page is really up to you. All I know is, popping up my to-do list works for me as motivation to get something done. I took a couple extra steps and ensured that only my local machine could get to that page, so folks on my local network couldn’t be popping up Things all day long by hitting the right IP in their browser. Other than that, I haven’t wanted to do anything fancier. That’s not really the point, after all.

Incidentally, I’ve found that limiting my consumption of distracting domains to the iPhone is a good way of regulating my time. If I have my iPhone in hand for more than a minute or two, I’m probably waiting around for something, in which case it wouldn’t hurt to see what’s up on [Hacker News](http://news.ycombinator.com/). Because reading on the iPhone isn’t optimal, I’m not likely to get lost in a sea of interesting links for an hour or two.
