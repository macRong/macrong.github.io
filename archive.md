---
layout: page
title: "文章归档"
permalink: /archive/
---

{% for post in site.posts %}
  {% assign current_year = post.date | date: "%Y" %}
  {% if current_year != previous_year %}
    <h2>{{ current_year }}</h2>
    {% assign previous_year = current_year %}
  {% endif %}
  <li>
    {{ post.date | date: "%m-%d" }}
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}