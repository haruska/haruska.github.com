---
layout: post
title: Polymorphic Include Plugin Updated
---

I spent some time over the past two days cleaning up the [polymorphic_include](http://github.com/haruska/polymorphic_include) plugin. The most significant was adding unit tests.

I wrote it a year ago so that I could eager load polymorphic associations using :include directives in ActiveRecord. This is mostly useful in a search results page.

Adding tests presented an interesting challenge because it is coded as a rails plugin. It's pretty nasty to test because it uses alias_method_chain to modify the calls to :find and :find_every when a polymorphic exception is thrown.

It isn't as useful for Rails versions greater than 2.1 because they've mostly addressed this issue. However, some queries still throw exception and this plugin tries to correct that. See the README file for more info. 
