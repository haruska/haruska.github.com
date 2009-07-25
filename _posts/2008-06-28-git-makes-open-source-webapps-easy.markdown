--- 
layout: post
typo_id: 41
title: git makes open source webapps easy
---
I actively try and open source as much of my code as possible. I've recently found I'm writing more and more mini-webapps in rails. With subversion these were very hard to share with the public.

It mostly comes down to secrets. You don't want to share your database.yml file, etc. But how do you share the project, without screwing up deployments and without giving up secrets? How many hoops do you really want to jump through to give away your code?

Well, git removes all of those hoops. With multiple remote repositories, it's trivial to have a remote repo that is open source and another that is private. Just point your production server to the private git repo for its code and you're good to go.

[fb2twit](http://github.com/haruska/fb2twit/tree/master), a small facebook app that posts status updates to twitter when entered in facebook, is open sourced on github.
