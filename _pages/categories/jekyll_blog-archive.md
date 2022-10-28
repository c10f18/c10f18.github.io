---
layout: archive
title: "Jekyll blog"
collection: jekyll_blog
permalink: /categories/jekyll_blog-archive
type: archive
---

{% assign posts = site.categories.study %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
