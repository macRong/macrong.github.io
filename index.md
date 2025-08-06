---
layout: home
title: 首页
---

<!-- 首页标题和简介（简洁风格） -->
<div class="home-intro">
  <h1>我的开发搞钱记录</h1>
  <p>分享技术开发经验与搞钱思路，专注于实用干货</p>
</div>

<!-- 最新文章列表 -->
<div class="post-list-short">
  <h2>最新文章</h2>
  {% for post in site.posts limit:5 %}  <!-- 只显示最新5篇 -->
    <article class="post-item">
      <!-- 文章日期 -->
      <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">
        {{ post.date | date: "%Y-%m-%d" }}
      </time>
      
      <!-- 文章标题 -->
      <h3>
        <a href="{{ post.url | relative_url }}" class="post-link">
          {{ post.title }}
        </a>
      </h3>
      
      <!-- 简短摘要（可选） -->
      {% if post.description %}
        <p class="post-excerpt">{{ post.description | truncate: 100 }}</p>
      {% endif %}
    </article>
  {% endfor %}

  <!-- 查看更多按钮 -->
  <div class="view-more">
    <a href="/archive/" class="btn">查看全部文章</a>
  </div>
</div>
