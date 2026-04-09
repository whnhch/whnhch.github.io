---
layout: page
permalink: /challenge/cloud/
title: Application Practice Logs
nav: false
---

## {% include repo_code_badge.liquid %} Application Practice & Deployment

{% assign challenge_cloud_collection = site.collections | where: "label", "challenge_cloud" | first %}
{% assign challenge_cloud_posts = challenge_cloud_collection.docs | sort: "date" | reverse %}

<div class="post-list">
{% for post in challenge_cloud_posts %}
<div class="post-item" style="padding: 15px; margin-bottom: 15px; border-left: 4px solid #8ce99a; background-color: rgba(211, 249, 216, 0.1); border-radius: 8px;">
  <h4 style="margin: 0 0 8px 0;">
    <a href="{{ post.url }}">{{ post.title }}</a>
  </h4>
  <small style="color: var(--global-text-color-light);">
    📅 {{ post.date | date: "%B %d, %Y" }}
    {% if post.tags %}
      | 🏷️ {% for tag in post.tags %}<span style="background-color: #d3f9d8; padding: 2px 8px; border-radius: 4px; margin-right: 5px;">{{ tag }}</span>{% endfor %}
    {% endif %}
  </small>
  <p style="margin: 8px 0 0 0; color: var(--global-text-color);">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
</div>
{% endfor %}

{% if challenge_cloud_posts.size == 0 %}
<p style="text-align: center; color: var(--global-text-color-light); padding: 30px;">
  No posts yet. 
</p>
{% endif %}
</div>

<hr style="margin-top: 40px; margin-bottom: 40px;">

<a href="/challenge/" class="btn btn-sm z-depth-0" role="button">← Back to Challenge Home</a>
