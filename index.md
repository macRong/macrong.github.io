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

