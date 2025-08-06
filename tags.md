---
layout: page
title: "所有标签"
permalink: /tags/
---

<!-- 遍历所有标签并显示对应文章 -->
{% for tag in site.tags %}
  <h3 id="{{ tag[0] }}">{{ tag[0] }}</h3>  <!-- 标签名 -->
  <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>  <!-- 文章链接 -->
        <small>{{ post.date | date: "%Y-%m-%d" }}</small>  <!-- 发布日期 -->
      </li>
    {% endfor %}
  </ul>
{% endfor %}