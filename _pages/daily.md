---
layout: single
title: "RecSys 日报"
permalink: /daily/
author_profile: true
toc: false
---

<style>
.daily-wrap { margin-top: 0.5em; }
.daily-card {
  display: block;
  border: 1px solid #e1e4e8;
  border-left: 4px solid #0366d6;
  border-radius: 6px;
  padding: 1em 1.2em;
  margin-bottom: 1em;
  background: #ffffff;
  transition: box-shadow .2s ease, transform .15s ease;
}
.daily-card:hover {
  box-shadow: 0 4px 14px rgba(0,0,0,.10);
  transform: translateY(-2px);
  text-decoration: none;
}
.daily-date {
  font-size: 1.15rem;
  font-weight: 700;
  color: #0366d6;
  margin-bottom: .35em;
}
.daily-excerpt {
  color: #444d56;
  font-size: .92rem;
  line-height: 1.55;
  margin-bottom: .4em;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.daily-more {
  color: #586069;
  font-size: .85rem;
  font-weight: 600;
}
.daily-empty { color: #6a737d; }
</style>

<p class="daily-wrap">每日自动更新的推荐算法 arXiv 论文日报：从 <code>cs.IR</code>、<code>cs.LG</code>、<code>stat.ML</code> 最近更新中筛选，下载全文后由大模型深度阅读并撰写总览、总结与点评。按日期倒序排列。</p>

{% assign items = site.daily | sort: 'date' | reverse %}
{% if items.size == 0 %}
  <p class="daily-empty">还没有日报，稍后再来看看。</p>
{% else %}
  {% for post in items %}
  <a class="daily-card" href="{{ post.url }}">
    <div class="daily-date">{{ post.date | date: "%Y 年 %m 月 %d 日" }}</div>
    <div class="daily-excerpt">{{ post.excerpt | strip_html | strip_newlines | truncate: 200 }}</div>
    <div class="daily-more">阅读全文 →</div>
  </a>
  {% endfor %}
{% endif %}
