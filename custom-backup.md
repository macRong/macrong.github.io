### 1.显示文章列表

<!-- 保留文章列表（可选） -->
{% for post in paginator.posts %}

  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.description }}</p>
  <small>{{ post.date | date: "%Y-%m-%d" }} · {{ post.categories | join: " / " }}</small>
{% endfor %}

### 2.临时备份
---
# Only the main Sass file needs front matter (the dashes are enough)
---

@import
  "minima/skins/{{ site.minima.skin | default: 'classic' }}",
  "minima/initialize";



/* 版权信息居中 */
.copyright {
  text-align: center;
  margin: 1rem 0; /* 可选：添加上下间距 */
}


### 3.index.md
---
layout: home  # 使用首页布局
---


一人AI开发公司，专注搞钱

{% for post in paginator.posts %}

  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.description }}</p>
  <small>{{ post.date | date: "%Y-%m-%d" }} · {{ post.categories | join: " / " }}</small>
{% endfor %}

---

## 📝 Blog

- [How I built this site](https://yourusername.github.io/blog/how-i-built)
- [Best GitHub Pages tips](https://yourusername.github.io/blog/github-pages-tips)

---

## 🔧 Projects

- [**CoolApp**](https://github.com/yourusername/coolapp) – Mobile app with offline sync.
- [**DevKit**](https://github.com/yourusername/devkit) – Toolkit for developers.

---

## 📬 Contact

- [Email](mailto:your@email.com)
- [Twitter](https://twitter.com/yourhandle)
- [blog](https://macrong.github.io/macRong/)


