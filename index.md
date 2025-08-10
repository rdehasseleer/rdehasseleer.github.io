---
layout: default
title: "Accueil"
---

<h1>Very (very) technical stuff</h1>
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date: "%d/%m/%Y" }}
    </li>
  {% endfor %}
</ul>
