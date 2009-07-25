--- 
layout: post
typo_id: 43
title: ninja-decorators
---
A couple of us at SnapMyLife were a bit surprised you couldn't easily use around\_filters outside of rails for general ruby programs, so we implemented them and put it up on github. We called the gem [ninja-decorators](http://github.com/haruska/ninja-decorators/tree/master), mostly in a mocking sense that everything seems to be rockstars and cool_fu these days. To install the gem:

    gem sources -a http://gems.github.com
    sudo gem install haruska-ninja-decorators

Here is a simple example:

    require 'rubygems'
    require 'ninja_decorators'

    class NinjaClass
      include NinjaDecorators

      attr_accessor :ret

      around_filter :common_around, [:foo, :bar]

      def foo
        @ret += "foo"
      end

      def bar
        @ret += "bar"
      end

      private

      def common_around
        @ret = "common "
        yield
        @ret += " around"
      end
    end

produces

    irb(main):076:0> n = NinjaClass.new
    => #<NinjaClass:0x220decc>
    irb(main):077:0> n.bar
    => "common bar around"
    irb(main):078:0> n.foo
    => "common foo around"
    
We'll add before\_filter and after\_filter soon.
