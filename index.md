---
layout: home  # Minima 主题默认首页布局，也可用 `layout: default` 自定义
title: 首页
---

<!-- 遍历 _posts 文章，按时间倒序展示 -->
{% for post in site.posts %}
  <article class="post">
    <!-- 文章日期 -->
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">
      {{ post.date | date: "%b %d, %Y" }}  <!-- 格式：May 20, 2016 -->
    </time>
    
    <!-- 文章标题 -->
    <h2 class="post-title">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    
    <!-- 文章内容（自动截取或用 excerpt） -->
    <div class="post-content">
      {{ post.content | strip_html | truncate: 200 }}  <!-- 纯文本截取200字符 -->
      <!-- 或用文章 Front Matter 里的 excerpt：{{ post.excerpt }} -->
    </div>
  </article>
{% endfor %}