---
layout: "archive"
permalink: /data-structure/
title: "Data Structure Posts by Tags"
author_profile: true
header:
  image: "/assets/images/classification-of-data-structure.png"
---

<ul class="posts">
{% assign count = 0 %}
{% for post in site.posts %}
  {% if post.tags contains 'data' %}
    {% if count < 20 %}
      {% assign count = count|plus:1 %}
      <div class="post_info">
        <li>
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span>({{ post.date | date:"%Y-%m-%d" }})</span>
        </li>
      </div>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>
