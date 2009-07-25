--- 
layout: post
typo_id: 6
title: Ubuntu MPlayer not detecting end of stream
---
There is a bug in the Ubuntu multiverse version of MPlayer that bit me when trying to write the <a href="http://haruska.com/documents/a-better-all-songs-considered-podcast/" title="ASC Podcast">All Songs Considered script for Linux</a>. At the end of the Real Audio stream, MPlayer continues to dump empty frames into the output file instead of exiting. This does not happen if you compile mplayer yourself with version 1.0RC1.

I recommend compiling from source if you're attempting to record streaming audio.
