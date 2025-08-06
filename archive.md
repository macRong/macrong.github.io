---
layout: page
title: "文章归档"
permalink: /archive/
---

{% for post in site.posts %}  <!-- 关键：遍历所有文章 -->
  {% assign current_year = post.date | date: "%Y" %}
  {% if current_year != previous_year %}
    <h2>{{ current_year }}</h2>  <!-- 按年份分组 -->
    {% assign previous_year = current_year %}
  {% endif %}
  <li>
    <time datetime="{{ post.date | date_to_xmlschema }}">
      {{ post.date | date: "%m-%d" }}  <!-- 显示月-日 -->
    </time>
    <a href="{{ post.url }}">{{ post.title }}</a>  <!-- 文章链接 -->
  </li>
{% endfor %}