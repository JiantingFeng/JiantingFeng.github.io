---
layout: page
permalink: /blog/
title: Blog
description: Thoughts, ideas, and research notes
nav: true
nav_order: 3
---

## Latest Posts

{% for post in site.posts %}
  <div class="post-preview">
    <h2 class="post-title">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    <div class="post-meta">
      <span class="post-date">{{ post.date | date: "%B %-d, %Y" }}</span>
      {% if post.tags.size > 0 %}
        <span class="post-tags">
          {% for tag in post.tags %}
            <a href="{{ '/blog/tag/' | append: tag | relative_url }}">#{{ tag }}</a>
          {% endfor %}
        </span>
      {% endif %}
    </div>
    <div class="post-excerpt">
      {{ post.excerpt | strip_html | truncatewords: 50 }}
    </div>
  </div>
  <hr>
{% endfor %} 