---
layout: archive
title: "Study"
collection: study
permalink: /categories/study-archive
type: archive
---

{% assign posts = site.categories.study %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}