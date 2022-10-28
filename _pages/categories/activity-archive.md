---
layout: archive
title: "Activity"
collection: activity
permalink: /categories/activity-archive
type: archive
---

{% assign posts = site.categories.activity %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
