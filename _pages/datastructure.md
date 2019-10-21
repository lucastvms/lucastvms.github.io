---
layout: "archive"
permalink: /data-structure/
title: "Data Structure Posts by Tags"
author_profile: true
header:
  image: "/assets/images/classification-of-data-structure.png"
---
<h2>teste c</h2>
{%- for post in site.categories[post] -%}
  {% include archive-single.html %}
{%- endfor -%}
