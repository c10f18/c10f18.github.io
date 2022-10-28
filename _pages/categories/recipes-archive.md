---
layout: archive
title: "Recipes"
collection: recipes
permalink: /categories/recipes-archive
type: archive
---

{% assign posts = site.categories.recipes %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
