---
layout: archive
permalink: /data-structure/
title: "Data Structure Posts"
author_profile: true
header:
  image: "/assets/images/classification-of-data-structure.png"
---
{% for post in site.categories['data'] %}
  {% include archive-single.html %}
{% endfor %}

<!--
<ul class="posts">
{% assign count = 0 %}
{% for post in site.posts %}
  {% if post.categories contains 'data', 'post'  %}
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
-->
