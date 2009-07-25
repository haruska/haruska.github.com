--- 
layout: post
typo_id: 48
title: "Mashery: Post-Mortem"
---
I work for a small VC-backed company in the mobile social media space. Something we want to offer is a public API to open up our community to development of 3rd party tools. Although we have the technical capabilities to build an infrastructure in-house, I had a look at <a href="http://mashery.com/">Mashery</a> to outsource some of the ongoing work. We were looking for:

* proxy front end that can scale up as our API use grows and have a caching strategy to reduce the load on our servers
* ability to throttle on a per app (or developer key) basis to anticipate server load
* developer documentation that is easy to update and publish, skinned to look like our site
* ability for developer feedback
* analytics on the usage of the API
* OAuth support

Looking at Mashery's offering, they seemed like a good fit. That was a month ago. Today, none of those things are fully baked. Nothing of their offering is self-service so everything requires customization. Most tasks run serially and take a minimum of 3-5 business days.

We should have known at the beginning. After the website erred out on purchase attempt, I was assigned an account rep who wanted to set up a conference call. After attempting to explain their cost as a "request per second per developer key", I counted them out. That type of pricing model wouldn't work with us mainly because all of our installs of, say, an iPhone app would have the same developer key. That prompted <a href="http://twitter.com/haruska/status/1858461676">this tweet</a>.

To be fair, the CEO got right back to me (as a side note, I guess it proves Twitter is a good way to get feedback to a company.) He seemed as confused as I was and explained they were changing their pricing model *that day*. Long story short, we signed up on a monthly basis based on the new, more straightforward pricing scheme (they've yet to publish as of this writing.) 

One point of contention was OAuth was not a part of their standard package. It was considered an advanced custom feature. It was odd because OAuth is quickly becoming the best practice for accessing user generated content. I would expect a market leader to be driving best practices, not behind on them.

However, OAuth alone would double the monthly fee and require a custom $2500 setup. We decided to implement that ourselves. Again, it isn't that we couldn't, we just didn't want to spend the time. This also complicated matters. Now we'd have to pass valid consumer keys to Mashery so they could still perform their throttling function. This never happened...we weren't able to get to this discussion before aborting the relationship.

Next pain point was on the skinned development documentation. It took them over a week to "provision" us a portal. And when they did, it wasn't skinned. After pointing back to the contract, our rep agreed to skin the portal. We sent over a screenshot and was told it would be skinned in 7-10 business days. In short, don't expect public facing documentation for three weeks after your first monthly payment.

The next hurdle was reporting. Our rep attempted to explain to us their wacked-out URI-based reporting scheme. You had to define which parts of your URL path was important to your calls. Long story short, they don't support Ruby on Rails RESTful type urls. For example, they couldn't figure out how to make these different calls for reporting:

* /pictures.xml
* /pictures/39290.xml
* /pictures/39290/comments.xml

The first one is a collection of all pictures. The second is retrieving the single picture with ID 39290. The last one is retrieving the comments attached to the picture 39290. I guess the problem was with ID wildcarding.

Because of this "unusual" URL scheme, we were given a statement of work for $1000 and *five* business days to implement what amounts to a regular expression in your code. We were told repeatedly that *no* customer has asked for anything so strange in reporting.

<strike>So, we refused to pay the ransom and asked for a refund. They've refused the refund. Apparently, they consider us "2 days from success". We're out a couple of thousand dollars and a month's headache for the effort. At least we figured it out early. I would suggest having them prove themselves to you before plunking down any money. At the least, ask for a 30-day guarantee. Don't let them develop their 1/2 baked product on your dime. </strike>

**Update 6/18/09**

After much back and forth with Mashery on twitter and email they have agreed to refund our money. They were gracious and took the time to understand our frustrations. In the end we have different opinions of how the process should work but I think we both have a better understanding of where each other are coming from.


