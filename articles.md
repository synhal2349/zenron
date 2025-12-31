---
layout: default
title: articles
permalink: /articles/
---

## 記事一覧

{% if site.articles and site.articles.size > 0 %}
<div class="articles-list">
  {% assign sorted_articles = site.articles | sort: 'date' | reverse %}
  {% for article in sorted_articles %}
  <article class="articles-item">
    <h3><a href="{{ article.url | relative_url }}">{{ article.title }}</a></h3>
    <p class="articles-meta">
      <time datetime="{{ article.date | date_to_xmlschema }}">
        {{ article.date | date: "%Y年%m月%d日" }}
      </time>
      {% if article.author %}
      • {{ article.author }}
      {% endif %}
    </p>
    {% if article.excerpt %}
    <div class="articles-excerpt">
      {{ article.excerpt }}
    </div>
    {% endif %}
    {% if article.tags %}
    <div class="articles-tags">
      {% for tag in article.tags %}
      <span class="tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
  </article>
  {% endfor %}
</div>
{% else %}
<p>まだ記事がありません。</p>
{% endif %}
