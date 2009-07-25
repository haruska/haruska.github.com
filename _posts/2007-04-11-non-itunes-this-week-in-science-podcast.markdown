--- 
layout: post
typo_id: 14
title: non-iTunes This Week in Science podcast
---
I'm a fan of the This Week in Science (TWiS) podcast. However, there are only two ways to get it: an iTunes feed and an email. In the email contains a link to a feedburner mp3 file. Why in the world they don't simply have an RSS feed is beyond me.

The nice thing about this little hack is we're just linking to the content, not actually redistributing it (similar to linking on a webpage), so it should avoid most copyright issues.

The script I have in mind should be simple:

1. Procmail forwards the weekly email to a script
2. The script parses out the mp3 link and updates an RSS XML file on the server

That's it folks. Anyone should be able to subscribe. I'll post the code and a link to my working version on both my blog and the TWiS forums when finished.
