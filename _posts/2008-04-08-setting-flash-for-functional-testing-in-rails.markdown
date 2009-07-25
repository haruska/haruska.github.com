--- 
layout: post
typo_id: 38
title: setting flash for functional testing in rails
---
This was hard to track down. For some reason I can't find the method definition of the `get` function for functional tests in rails (anyone?).

Anyway, it is:

    get(action, parameters={}, session={}, flash={})

so, you can set a flash for a test action (example):

    get :index, {}, {}, {:notice => "Test Flash"}
