---
layout: home  # 使用首页布局
---

<!-- 这里添加自定义内容，如欢迎语、分类导航等 -->
# 欢迎来到我的博客
分享技术心得与生活感悟...

<!-- 保留文章列表（可选） -->
{% for post in paginator.posts %}
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.description }}</p>
  <small>{{ post.date | date: "%Y-%m-%d" }} · {{ post.categories | join: " / " }}</small>
{% endfor %}