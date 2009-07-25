--- 
layout: post
typo_id: 5
title: A Better All Songs Considered Podcast
---
<strong>Download</strong>

<a href="http://svn.haruska.com/scripts/all_songs_considered/allsongs_mac.py" title="ASC Mac python script">Python script (Mac OS X) </a> -or- <a href="http://svn.haruska.com/scripts/all_songs_considered/allsongs_linux.py">Python script (Linux)</a>

<strong>Requirements</strong>
<ul>
<li><a href="http://www.python.org/download/releases/2.4.4/">Python 2.4</a></li>
<li><a href="http://www.mplayerhq.hu/design7/news.html">MPlayer</a> (with command line enabled)</li>
<li><a href="http://www.audiocoding.com/">faac </a>encoder (OS X) -or- <a href="http://lame.sourceforge.net">lame</a> encoder (Linux)</li>
<li>Apple's proprietary <a href="http://homepage.mac.com/applepodcast/podcasts/Resources/static/podcast_chapter_tool_beta.dmg">ChapterTool</a> (OS X only)</li>
<li><a href="http://atomicparsley.sourceforge.net/">AtomicParsley</a> (OS X only)</li>
</ul>
<strong>Description</strong>

<a href="http://www.npr.org">National Public Radio</a>'s music program <a href="http://www.npr.org/programs/asc/"><em>All Songs Considered </em></a>is a great weekly program that features new (mostly) adult alternative music. NPR has started publishing a <a href="http://www.npr.org/rss/podcast/podcast_detail.php?siteId=4819413">podcast of the show</a> but it leaves a bit to be desired. The ASC website is much more useful. You can get a blurb about the band and song along with the ability to stream each song individually to see if it is in your tastes. How can we make the podcast more useful like the website? To start, we can split it into tracks, with the artist and song title encoded in each. Album art for each track would be a nice bonus.

The Mac script creates an "enhanced" podcast which is a single m4a file with chapters and meta info. Unfortunately, Apple decided to release their chapter tool OS X only so this doesn't work for the majority of people. Still, it is pretty good and it probably what ASC should move to

The Linux script is currently what I use. It creates an mp3 file for each track and encodes it. I then put that in a playlist on my iPod every week. Not exactly a "podcast" because it is many files, but has some benefits over the OS X version because you can change all the meta-data for each song.
