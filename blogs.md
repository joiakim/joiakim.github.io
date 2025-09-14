---
layout: default
title: Blogs
---

<div class="center-content">
  # My Technical Blogs

  Here are my latest posts:
</div>

{% for post in site.posts %}
  - [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
