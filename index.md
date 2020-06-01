---
layout: default  
title: Home  
navigation_weight: 1  
---

# Welcome to Code Shenanigans Blog

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
