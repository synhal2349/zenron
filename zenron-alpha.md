---
layout: no-header
title: ZENRON[α] - ZEN大学の歩き方
custom_css: /assets/css/alpha-style.css
google_fonts: https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+New:wght@500;700;900&display=swap
permalink: /zenron-alpha/
show_sidebar: false
---

<!-- ① ヒーローセクション -->
<section class="theme-section">
  <div class="background-video">
    <img src="{{ '/assets/images/alpha-back.png' | relative_url }}" alt="背景画像">
  </div>

  <div class="theme-message-area">
    <h2 class="theme-title">
      <span class="word-fadein" style="animation-delay: 0.5s;">ZENRON[α]</span>
    </h2>
    <p class="theme-subtitle">
      <span class="word-slideup" style="animation-delay: 1.5s;">テーマ：「ZEN大学の歩き方」</span>
    </p>
    <div class="theme-statement">
      <p class="theme-quote" style="animation-delay: 2.0s;">ZEN大学は2025年に開学した新しい大学だ。</p>
      <p class="theme-quote" style="animation-delay: 2.5s;">ネットで完結する大学だから足を使って学び歩く必要はない。</p>
      <p class="theme-quote" style="animation-delay: 3.0s;">それでも「学生として学ぶ」ための歩き方は考えてみる必要があると思う。</p>  
      <p class="theme-quote lead-in" style="animation-delay: 4.0s;">
        ZENRON[α]はそういった<br>
        ZEN大学という、世界中に広がる"ネットワーク"としての<br>大学の歩き方を提案する。
      </p>
    </div>
    <div class="theme-action" style="animation-delay: 5.5s;">
      <p>いつかZEN大学を飛び出し、世界を自由自在に歩く僕らと<br>歩き方の練習をやってみよう。</p>
    </div> 
  </div>
</section>

<!-- ② 記事一覧（元のまま） -->
<section class="articles-grid-section">
    {% assign target_tag = "α" %}
    {% if site.articles and site.articles.size > 0 %}
        {% assign filtered_by_tag = site.articles | where_exp: "item", "item.tags contains target_tag" %}
        {% if filtered_by_tag.size > 0 %}
            {% assign sorted_articles = filtered_by_tag | sort: 'date' | reverse %}
            <h2 class="section-heading">タグ：{{ target_tag }} の記事一覧</h2>
            <div class="articles-grid">
                {% for article in sorted_articles limit:4 %}
                <a href="{{ article.url | relative_url }}" class="articles-panel">
                    <div class="image-wrapper">
                        {% if article.thumbnail %}
                        <img src="{{ '/assets/images/' | append: article.thumbnail | relative_url }}" alt="{{ articles.title }}">
                        {% else %}
                        <img src="{{ '/assets/images/default-thumb.jpg' | relative_url }}" alt="{{ article.title }}">
                        {% endif %}
                    </div>
                    <div class="articles-info">
                        <p class="article-title">{{ article.title }}</p>
                        <p class="articles-meta">
                            {{ article.date | date: "%Y.%m.%d" }}<br>
                            {{ article.excerpt | strip_html | truncate: 40 }}
                        </p>
                    </div>
                </a>
                {% endfor %}
            </div>
        {% else %}
            <h2 class="section-heading">タグ：{{ target_tag }} の記事はありません</h2>
        {% endif %}
    {% else %}
        <h2 class="section-heading">記事データが存在しません</h2>
    {% endif %}
</section>
