### 1.显示文章列表

<!-- 保留文章列表（可选） -->
{% for post in paginator.posts %}

  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.description }}</p>
  <small>{{ post.date | date: "%Y-%m-%d" }} · {{ post.categories | join: " / " }}</small>
{% endfor %}