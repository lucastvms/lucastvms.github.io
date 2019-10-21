---
layout: "archive"
permalink: /data-structure/
title: "Data Structure Posts by Tags"
author_profile: true
header:
  image: "/assets/images/classification-of-data-structure.png"
---
novo

{% assign count = 0 %}
{% for post in site.posts %}
  {% if post.categories contains 'j', 'data' %}
    {% if count < 20 %}
      {% assign count = count|plus:1 %}
      {% include archive-single.html %}
    {% endif %}
  {% endif %}
{% endfor %}
