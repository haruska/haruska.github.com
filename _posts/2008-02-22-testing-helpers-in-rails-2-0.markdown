--- 
layout: post
typo_id: 34
title: testing helpers in rails 2.0
---
I've been testing helper classes in rails using the method from the [Rails Recipes book](http://www.pragprog.com/titles/fr_rr/). That seems to be broken in rails 2.0 since @params and @request are no longer accessible in controllers. Luckily I also use [mocha](http://mocha.rubyforge.org/) for mocks and stubs, so this was a quick fix.

So, the new code for testing rails helpers is (for me anyway):

    require File.dirname(__FILE__) + '/../test_helper'

    class ApplicationHelperTest < Test::Unit::TestCase
      include ActionView::Helpers::UrlHelper
      include ActionView::Helpers::TextHelper
      include ActionView::Helpers::TagHelper
      include ApplicationHelper

      def setup
        @controller = HomeController.new
        request = ActionController::TestRequest.new
        @controller.expects(:params).returns(Hash.new)
        @controller.expects(:request).returns(request)
        @controller.send(:initialize_current_url)
      end

      ...tests...
    end
