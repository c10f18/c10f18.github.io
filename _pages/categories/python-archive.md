---
layout: archive
title: "Python"
collection: python
permalink: /categories/python-archive
type: archive
---

{% assign posts = site.categories.python %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
