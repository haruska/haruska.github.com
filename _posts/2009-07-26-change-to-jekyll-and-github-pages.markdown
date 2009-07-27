---
layout: post
title: Change to Jekyll and Github Pages
---

It seems a lot of geeks with a blog tend to spend more time changing the supporting software and layout of the site more than just writing posts. I am no exception. This weekend I followed in the footsteps of coworkers [nirvdrum](http://nirvdrum.com) and [graysky](http://graysky.org) and converted my blog to [Jekyll](http://github.com/mojombo/jekyll/tree/master). I actually took the additional step of no longer hosting it myself, instead prefering the ease of [github pages](http://pages.github.com/). Here's what I did to move away from a self-hosted Typo blog

### Fork the mojombo.github.com project ###

It's a [good example site](http://github.com/mojombo/mojombo.github.com/tree/master) that is under MIT license (except the content itself of course). Added benefit is you don't have to mess around with the layout just yet.

1. Delete all copyrighted content
2. Change Tom's information to yours where applicable
3. Change the CNAME to yourdomain.com

<p></p>

### Migrate posts from Typo ###

I had to make some changes to mojombo's converter for typo 5+. So, grab my version of jekyll or patch your gem install. [Here is the diff](http://github.com/haruska/jekyll/commit/47cd66244c6de2e90bf0d9f4d78c87dcb3e22032)

With the changes applied, the migration is pretty straight forward.

### Modify permalinks and update feedburner ###

Modify your permalinks in jekyll to match your old typo install so readers don't lose their way.

### Check in all changes to github ###

You should change your project name to <github-username>.github.com and commit those chages up to github. Also, FYI you need a paid account for CNAMEs to work on github.

### Update your domain's DNS ###

You need two entries

1. A-record yourdomain.com to 65.74.177.129 
2. Cname www.yourdomain.com to yourdomain.com


That should be all you need to get started. I'd recommend changing your layout so your blog doesn't continue to look like mojombo's blog. However, this isn't strictly necessary.
