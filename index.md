---
layout: home
author_profile: true
header:
  image: "/assets/images/index-header-image.jpg"
---
<h2>teste g</h2>
<ul class="posts">
{% for post in site.posts %}
    <div class="post_info">
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span>({{ post.date | date:"%Y-%m-%d" }})</span>
      </li>
    </div>
{% endfor %}
</ul>
