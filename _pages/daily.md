---
layout: single
title: "RecSys 日报"
permalink: /daily/
author_profile: true
toc: false
---

<p class="daily-intro">
  每日自动更新的推荐算法 arXiv 论文日报：从 <code>cs.IR</code>、<code>cs.LG</code>、<code>stat.ML</code> 最近更新中筛选，下载全文后由大模型深度阅读并撰写总览、总结与点评。按日期倒序排列。
</p>

{% assign items = site.daily | sort: 'date' | reverse %}
{% if items.size == 0 %}
还没有日报，稍后再来看看。
{% else %}
<div class="daily-list">
  {% for post in items %}
  {% assign overview = post.content | split: '## 论文列表' | first | replace: '## 总览', '' %}
  <div class="daily-card">
    <a class="daily-card__link" href="{{ post.url }}">
      <span class="daily-card__date">{{ post.date | date: "%Y 年 %m 月 %d 日" }}</span>
      <span class="daily-card__excerpt">{{ overview | strip_html | strip_newlines | truncate: 220 }}</span>
      <span class="daily-card__more">阅读全文 <span aria-hidden="true">→</span></span>
    </a>
  </div>
  {% endfor %}
</div>
{% endif %}
