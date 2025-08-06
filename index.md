---
layout: home
---

<!-- 保留主题默认的文章列表渲染 -->
<!-- {{ content }} -->

<!-- 直接使用 Minima 主题自带的文章循环逻辑 -->
<ul class="post-list">
  {% for post in site.posts %}
    <li>
      {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
      <span class="post-meta">{{ post.date | date: date_format }}</span>

      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      
      <!-- 显示文章摘要（主题默认支持） -->
      {% if site.show_excerpts %}
        {{ post.excerpt }}
      {% endif %}
    </li>
  {% endfor %}
</ul>

<!-- 主题默认的"订阅RSS"链接（可选保留） -->
<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
