---
layout: archive
title: "Motion Graphic"
collection: motion_graphic
permalink: /categories/motion_graphic-archive
type: archive
---

{% assign posts = site.categories.motion_graphic %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
