---
layout: default
title: Blogs
---

# My Technical Blogs

Here are my latest posts:

{% for post in site.posts %}
  - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %} 
