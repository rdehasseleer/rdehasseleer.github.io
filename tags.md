---
layout: default
title: "Tags"
---

<h1>Tags</h1>

<ul>
{% for tag in site.tags %}
  <li>
    <strong>{{ tag[0] }}</strong>
    <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <small>({{ post.date | date: "%Y-%m-%d" }})</small>
      </li>
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>
