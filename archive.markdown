---
layout: default
title: Post Archive
---

{% for post in site.posts %}
* <span>{{ post.date | date_to_string }}</span> &raquo; [{{post.title}}]({{post.url}})
{% endfor %}
