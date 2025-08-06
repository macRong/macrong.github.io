---
layout: page
title: "文章归档"
permalink: /archive/
---

<!-- 按年份归档所有文章 -->
{% for post in site.posts %}
  {% assign current_year = post.date | date: "%Y" %}
  {% if current_year != previous_year %}
    <h3>{{ current_year }}</h3>  <!-- 年份标题 -->
    {% assign previous_year = current_year %}
  {% endif %}
  <li>
    {{ post.date | date: "%m-%d" }}  <!-- 月-日 -->
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}