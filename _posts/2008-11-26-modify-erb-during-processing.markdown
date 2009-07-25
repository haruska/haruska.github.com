--- 
layout: post
typo_id: 3
title: modifying snippets of erb during processing
---
Today we ran into an interesting problem that turned out to have an elegant solution. We had a list of links that we wanted displayed as comma separated. Long story short, the resulting output contained spaces before the commas (i.e. Dick , Mary , and Jane). We wanted to take that output and run a regex replace on it.

Turns out this is pretty easy to do in rails. We added the following to our helper file

    def suppress_comma_spacing(&block)
      res = capture(&block)
      concat(res.gsub(/\s+,/m, ','), block.binding)
    end

then wrapped the code whose output needed modification in a code block in the erb file (trivial example below)

    <% suppress_comma_spacing do %>
      <%= link_to "Dick", user_path(dick) %>
      ,
      <%= link_to "Mary", user_path(mary) %>
      , and
      <%= link_to "Jane", user_path(jane) %>
    <% end %>

The result is Dick, Mary, and Jane with the spaces before the commas stripped. Capture allows you to get the processed erb from executing the block. Pretty useful.
