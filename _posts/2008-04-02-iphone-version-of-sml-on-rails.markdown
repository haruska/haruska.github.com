--- 
layout: post
typo_id: 36
title: iPhone version of SML on rails
---
This week we officially released the [iPhone version of SnapMyLife](http://iphone.snapmylife.com). This was fairly straightforward with [rails 2.0](http://www.rubyonrails.org/) and the [iui javascript framework](http://code.google.com/p/iui/).

Rails now uses custom formats as part of the incoming request. So I just added an "iphone" format and created views like "index.iphone.erb" where needed. This is really excellent MVC separation while allowing various versions of the site. 

It took a while to get used to the everything-is-an-ajax-request style of iui. Basically, there is a single DOM that you add nodes to as navigation is followed. The javascript then adjusts the DOM as you navigate through the site.

Development wasn't without snags. The most interesting problems had to do with Rails flash display and advertising on the device. I adjusted how iui handles the server respone. Now flash messages and a new html advert are passed along with the html data snippet. Javascript then breaks up the server response into its components and displays them properly using the iui DOM and CSS. I'll clean it up and post it if other Rails / iui projects are interested.
