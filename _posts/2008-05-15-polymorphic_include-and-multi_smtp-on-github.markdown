--- 
layout: post
typo_id: 39
title: polymorphic_include and multi_smtp on GitHub
---
I finally took the time to wrap up two useful pieces of code into Rails plugins. 

The first - [polymorphic_include ](http://github.com/haruska/polymorphic_include) - I've mentioned before. It allows you to eager load polymorphic associations. I've cleaned up the code, including fixes for some nasty eval memory leaks.

The second plugin - [multi_smtp](http://github.com/haruska/multi_smtp) - came about out of using gMail as our SMTP server for sending notifications on [SnapMyLife](http://www.snapmylife.com). Google [limits](http://mail.google.com/support/bin/answer.py?answer=22839&topic=12837) the number of messages per account and recommends you set up multiple accounts if you have to send more. This plugin allows you to define multiple accounts that Rails will spread the email load around.

Hope others find the plugins useful. These are my first experiments with [git](http://git.or.cz/) and [GitHub](http://github.com/), so I'm also seeing how easy it is for others to submit their ideas. I by no means want to be "keeper of the code" and like git's SCM style.

To start using git on OS X, download the dmg package from the [git google code page](http://code.google.com/p/git-osx-installer/).
