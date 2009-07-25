--- 
layout: post
typo_id: 29
title: mms2r and scRUBYt
---
One thing I never enjoyed doing as a developer is writing crawlers, parsers, and scrapers. They always seem flaky and by definition the node tree can change without warning. Luckily, there are developers out there that really love hacking at this stuff... and that makes **all** of our lives easier.

The first project I use all the time is [scRUBYt ](http://scrubyt.org/) which is primarily maintained by [Peter](http://www.technorati.com/people/technorati/peteronrails/). He is always willing to help out and we've contracted his work a few times at [Mobicious](http://www.mobicious.com). scRUBYt is like [Hpricot](http://code.whytheluckystiff.net/hpricot/) on steroids. It is trying to prevent the flakiness of your scripts along with trying to get you out of the XPath game. It works great for almost all dynamic websites. More importantly, when the site changes markup it is easy to re-run your learning scripts and update your crawlers.

The other project that I'm loving more and more is [mms2r](http://mms2r.rubyforge.org/). It is a ruby library that processes picture and video messages from mobile phones. We use it extensively for [SnapMyLife](http://www.snapmylife.com). I tell you sites like ours would be a bear to code without the grunt work of developers like [Matt Mondragon](http://blog.mondragon.cc). Mms2r a well thought out project that only requires you to add extra carrier templates if they do something odd. He's even helped me out with some fixes to templates I couldn't seem to get right myself.

Bottom line, it's the people behind the software that make it so enjoyable. Most small open source projects really are a team of one. Show them some support. You don't need to fix bugs (although that is appreciated), just give them feedback and try and help. Hell, write some documentation... every developer hates writing it and it is hard to know what the user needs help with.
