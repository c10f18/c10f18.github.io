---
layout: archive
title: "Algorithm"
collection: algorithm
permalink: /categories/algorithm-archive
type: archive
---

{% assign posts = site.categories.algorithm %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
