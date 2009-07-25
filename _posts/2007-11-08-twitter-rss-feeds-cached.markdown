--- 
layout: post
typo_id: 24
title: twitter rss feeds cached
---
It seems twitter is caching their RSS feeds for hours, kind of making them meaningless. I have a script that check for updates on my feed every 20 minutes and posts it to haruska.com if updated. Three hours after a tweet, and it still hasn't updated. I filed a bug, but no response.

The fix is just to screen scrape your feed instead of RSS. This has the effect of increasing server load on Twitter and complicating the users scripts. Don't companies think this stuff through? That was one of the points of an RSS feed.

Ah, well... I'll update my script and post it sometime tonight.
