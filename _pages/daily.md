---
layout: single
title: "RecSys 日报"
permalink: /daily/
author_profile: true
toc: false
---

每日自动更新的推荐算法 arXiv 论文日报：从 `cs.IR`、`cs.LG`、`stat.ML` 最近更新中筛选，下载全文后由大模型深度阅读并撰写总览、总结与点评。按日期倒序排列。

{% assign items = site.daily | sort: 'date' | reverse %}
{% if items.size == 0 %}
还没有日报，稍后再来看看。
{% else %}
{% for post in items %}
<div class="daily-card">
  <a href="{{ post.url }}">
    <div class="daily-date">{{ post.date | date: "%Y 年 %m 月 %d 日" }}</div>
    <div class="daily-excerpt">{{ post.excerpt | strip_html | strip_newlines | remove_first: "总览" | split: "论文列表" | first | truncate: 200 }}</div>
    <div class="daily-more">阅读全文 →</div>
  </a>
</div>
{% endfor %}
{% endif %}
