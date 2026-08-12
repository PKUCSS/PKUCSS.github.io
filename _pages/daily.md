---
layout: single
title: "RecSys 日报"
permalink: /daily/
author_profile: true
toc: false
---

<style>
.daily-card:hover { box-shadow: 0 4px 14px rgba(0,0,0,.12); transform: translateY(-2px); }
.daily-card { transition: box-shadow .2s ease, transform .15s ease; }
</style>

{% assign card = 'display:block;border:1px solid #e1e4e8;border-left:4px solid #0366d6;border-radius:6px;padding:1em 1.2em;margin-bottom:1em;background:#ffffff;text-decoration:none;' %}
{% assign date_style = 'font-size:1.15rem;font-weight:700;color:#0366d6;margin-bottom:.35em;' %}
{% assign excerpt_style = 'color:#444d56;font-size:.92rem;line-height:1.55;margin-bottom:.4em;' %}
{% assign more_style = 'color:#586069;font-size:.85rem;font-weight:600;' %}

每日自动更新的推荐算法 arXiv 论文日报：从 `cs.IR`、`cs.LG`、`stat.ML` 最近更新中筛选，下载全文后由大模型深度阅读并撰写总览、总结与点评。按日期倒序排列。

{% assign items = site.daily | sort: 'date' | reverse %}
{% if items.size == 0 %}
还没有日报，稍后再来看看。
{% else %}
{% for post in items %}
<a class="daily-card" href="{{ post.url }}" style="{{ card }}">
  <div style="{{ date_style }}">{{ post.date | date: "%Y 年 %m 月 %d 日" }}</div>
  <div style="{{ excerpt_style }}">{{ post.excerpt | strip_html | strip_newlines | remove_first: "总览" | split: "论文列表" | first | truncate: 200 }}</div>
  <div style="{{ more_style }}">阅读全文 →</div>
</a>
{% endfor %}
{% endif %}
