---
page_id: news
layout: page
title: News
permalink: /news/
---

<!-- 自定义 News 页面的样式 -->
<style>
/* 1. 修改 News 页面标题颜色 */
.page#news h1.page-title {
  color: #006e3c; /* HKU green，改这里即可 */
  margin-bottom: 0.2rem !important;
}

/* 2. 让标题下方有一条横线 */
.page#news h1.page-title::after {
  content: "";
  display: block;
  width: 100%;
  border-bottom: 1.5px solid #ccc;
  margin-top: 6px;
  margin-bottom: 12px;
}

/* 3. 减小每条 news 之间的间距 */
.news-list li {
  margin-bottom: 6px !important; /* 想更紧凑可以改为 4 或 2 */
  line-height: 1.3;
}
</style>

---

{% include news.liquid %}

<hr>

## News Archive (by Year)

{% assign items = site.news | sort: 'date' | reverse %}
{% assign groups = items | group_by_exp: 'item', 'item.date | date: "%Y"' %}

{% for year in groups %}

### {{ year.name }}

<ul>
  {% for item in year.items %}
    <li>
      <span style="color:#888">{{ item.date | date: "%Y-%m-%d" }}</span>
      — <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
    </li>
  {% endfor %}
</ul>
{% endfor %}
