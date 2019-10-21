---
layout: "archive"
permalink: /data-structure/
title: "Data Structure Posts by Tags"
author_profile: true
header:
  image: "/assets/images/classification-of-data-structure.png"
---
<h2>teste 1</h2>
{%- for post in site.tags[include.post] -%}
  {% include archive-single.html %}
{%- endfor -%}
