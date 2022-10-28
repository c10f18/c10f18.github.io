---
layout: archive
title: "JAVA"
collection: java
permalink: /categories/java-archive
type: archive
---

{% assign posts = site.categories.java %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
