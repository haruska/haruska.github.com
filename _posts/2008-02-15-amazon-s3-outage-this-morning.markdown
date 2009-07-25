--- 
layout: post
typo_id: 32
title: amazon s3 outage this morning
---
We moved [SnapMyLife](http://www.snapmylife.com) over to [amazon ec2 and s3 hosting](http://www.amazon.com/AWS-home-page-Money/b/ref=sc_iw_l_0?ie=UTF8&amp;node=3435361&amp;no=3435361&amp;me=A36L942TSJ2AJA) because we figured they're amazon, so hey what are the odds of them going down? According to their [SLA](http://www.amazon.com/b?ie=UTF8&amp;node=379654011) they claim a "3 nines" (99.9%) uptime per month. This actually means they're allowed .75 hours of downtime every month.  They were down for 4 hours today (so far).

I understand that things happen, and it wasn't so much the outage that [pissed everyone off](http://blogs.zdnet.com/projectfailures/?p=602), it was [the response](http://developer.amazonwebservices.com/connect/thread.jspa?messageID=79884&amp;tstart=0%2379884). They didn't post anything on the AWS website, you had to dig around the forums. Then, the only responses were "we're looking into it" and "it's been resolved". No ETA's ever.

I'm sure Amazon just lost some customers today, although we're not one of them. I just wish they'd have better communication on their end so we could relay to our customers.
