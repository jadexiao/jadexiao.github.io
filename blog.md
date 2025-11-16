---
layout: page
title: blog
permalink: /blog/
---

<ul class="post-list">
  {%- for post in site.posts -%}
  <li>
    <p class="post-link"><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></p>
    <p class="post-meta">
    <span>{{ post.date | date: "%B %-d, %Y" }}</span>
    ·
    <span>
      {% for tag in post.tags %}
        <a href="{{ site.baseurl }}/tag/{{ tag }}"><i class="fa-regular fa-hashtag"></i>{{ tag }}</a>
      {% endfor %}
    </span>
  </p>
  </li>
  {%- endfor -%}
</ul>
