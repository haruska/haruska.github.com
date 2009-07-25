--- 
layout: post
typo_id: 13
title: Internet radio stream time shifting
---
Download
--------------

* [podcast.sh](http://svn.haruska.com/scripts/radio_tivo/podcast.sh)
* [example crontab](http://svn.haruska.com/scripts/radio_tivo/crontab)

Requirements
--------------------

* MPlayer (with codecs)
* Bash
* Perl
* Cron

Description
----------------

There are some radio programs that I would like to have as podcasts on my commute. Not all of these are available as podcasts but all are on the air and on internet streaming radio. After looking around the internet, there doesn't seem to be much available. This [Linux Journal article](http://www.linuxjournal.com/article/8171) came really close, so I used that as a basis for my script. [StreamRipper](http://streamripper.sourceforge.net/) did not meet my needs since not all streams are mp3 based and it doesn't play nice with cron.

This script is able to:

* Record multiple streams simultaneously
* Transcode those streams to mp3
* Maintain an RSS 2.0 XML file

I modified the Linux Journal script to work on a shared host (Dreamhost, but any with a shell should work.) It was a pretty simple and all the credit should go to the original authors.

