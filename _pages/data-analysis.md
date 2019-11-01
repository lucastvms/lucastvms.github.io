---
layout: archive
permalink: /data-analysis/
title: "Data Analysis Posts"
author_profile: true
---
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/data-analysis/data-science.jpg)

{% for post in site.categories['data analysis'] %}
  {% include archive-single.html %}
{% endfor %}
