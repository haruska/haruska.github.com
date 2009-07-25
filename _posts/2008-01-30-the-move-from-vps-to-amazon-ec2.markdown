--- 
layout: post
typo_id: 28
title: the move from vps to amazon ec2
---
Today we moved [SnapMyLife](http://www.snapmylife.com) from [liquidweb](http://www.liquidweb.com/) virtual private servers (vps) to [Amazon's Elastic Compute Cloud](http://www.amazon.com/gp/browse.html?node=201590011) (ec2). This was made possible mostly because of the leg work of my co-worker [Matt Conway](http://simplygenius.com/). He has graciously shared his setup in the form of a Rails plugin called [rubber](http://rubyforge.org/projects/rubber/). I'll leave a discussion of rubber for another post, but if you're considering ruby on rails on ec2, Matt has made it pretty turn-key.

The obvious question is "why?" We never really had plans for SnapMyLife hosting. So far we've been piggy-backing off of mobicious hosting. Liquidweb is a great vps provider and if we wanted to go that route, we'd defiantly choose them again.

We ultimately went with ec2 because of the interesting possibilities. You now have the ability to, in essence, **script** hardware. You can programatically fire up more resources as you need them. Servers tend to get slammed from 5-7pm? Just double your capacity for that time. You can easily see moving away for buying enough hardware for the worst case scenario to planning for it with hardware on demand.

It has other implications for daily development. Testing on a true parallel system (for every developer) becomes possible. One script to create a clone of production servers, run your tests, and tear it down. Only costs a couple of bucks.

I've done some performance testing specifically for rails on ec2 that I'll clean up and publish, but Amazon has an acceptable performance for the price.

So, what are the downsides? I guess the biggest is a lack of IP address persistence. When you create an instance, it is assigned a public IP, but there is no guarantee that the instance will remain up or that on restart, you'll have the same address. This creates a problem for trying to run load balancers. However, we get around this with DNS round-robin and scripting updates. It isn't perfect, but it **is** an acceptable level of risk.

Bottom line is we're all happier. We don't have to re-investigate how much hardware we need each month. The usage dictates hardware and you only have to plan for about fifteen minutes in advance, not 24 hours.
