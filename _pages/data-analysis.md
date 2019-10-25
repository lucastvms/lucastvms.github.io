---
layout: archive
permalink: /data-analysis/
title: "Data Analysis Posts"
author_profile: true
---
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/data-analysis/steps.png)

{% for post in site.categories['data structure'] %}
  {% include archive-single.html %}
{% endfor %}
