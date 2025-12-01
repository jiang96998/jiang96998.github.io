---
page_id: news
layout: page
title: News
permalink: /news/
---


<div style="text-align:center;">
  <hr style="width:40%; border:1px solid #ccc;">
</div>

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