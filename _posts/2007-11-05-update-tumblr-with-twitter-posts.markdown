--- 
layout: post
typo_id: 23
title: update tumblr with twitter posts
---
I can't rave enough about [tumblr](http://tumblr.com). It is a great idea executed well by a small dev team.  I wanted my [twitter](http://twitter.com) updates to happen more frequently then their feed updates allow. I also wanted it to be formatted differently.

So, I wrote a quick [ruby script](http://svn.haruska.com/scripts/tumblr/twitter.rb) that grabs a twitter feed and updates tumblr with it. It changes the text to be "status: ..." instead of starting with your username. It also links back to the original tweet.

Add your username and password, stick it in your crontab and you should be good to go. You can see the results on [my tumble log](http://haruska.com)
