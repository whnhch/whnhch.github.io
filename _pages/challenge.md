---
layout: page
permalink: /challenge/
title: Challenge
nav: true
nav_order: 3
---

This is an archive of my **30-Day Research & Practice Challenge**. 
I am building my expertise in Databases, NLP, and related application practice, one day at a time.

<br>

### 🏃‍♂️ 30-Day Progress Board
<style>
.grid-container { display: grid; grid-template-columns: repeat(auto-fill, minmax(45px, 1fr)); gap: 10px; margin-top: 15px; margin-bottom: 30px; }
.grid-item { aspect-ratio: 1; border-radius: 8px; background-color: var(--global-bg-color, #f1f3f5); border: 1px solid var(--global-divider-color, #dee2e6); display: flex; align-items: center; justify-content: center; font-size: 0.9em; text-decoration: none !important; color: var(--global-text-color) !important; transition: all 0.2s; font-weight: bold; }
.grid-item.progress { background: linear-gradient(135deg, #ffe8cc 0%, #d0ebff 50%, #d3f9d8 100%); border-color: #999; }
.grid-item.opacity-20 { opacity: 0.2; }
.grid-item.opacity-60 { opacity: 0.6; }
.grid-item.opacity-100 { opacity: 1; }
.grid-item:hover { transform: translateY(-3px); box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
</style>

<div class="grid-container">
{% assign db_count = site.challenge_db | size %}
{% assign nlp_count = site.challenge_nlp | size %}
{% assign cloud_count = site.challenge_cloud | size %}
{% assign total_count = db_count | plus: nlp_count | plus: cloud_count %}
{% assign opacity_class = "opacity-20" %}

    {% if total_count >= 3 %}
        {% assign opacity_class = "opacity-100" %}
    {% elsif total_count == 2 %}
        {% assign opacity_class = "opacity-60" %}
    {% elsif total_count == 1 %}
        {% assign opacity_class = "opacity-20" %}
    {% endif %}

    {% if total_count > 0 %}
    <a href="/challenge/" class="grid-item progress {{ opacity_class }}" title="Progress: {{ total_count }} post(s) (DB: {{ db_count }}, NLP: {{ nlp_count }}, Practice: {{ cloud_count }})">1</a>
    {% else %}
    <div class="grid-item" title="Progress: 0 posts">1</div>
    {% endif %}

    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
    <div class="grid-item">7</div>
    <div class="grid-item">8</div>
    <div class="grid-item">9</div>
    <div class="grid-item">10</div>
    <div class="grid-item">...</div>
    <div class="grid-item">30</div>
</div>

<hr>

### 📂 Challenge Logs
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">📑 DB Papers</h5>
            <a href="/challenge/db/" class="btn btn-sm z-depth-0" role="button">Go to DB Logs</a>
        </div></div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">🧠 NLP Papers</h5>
            <a href="/challenge/nlp/" class="btn btn-sm z-depth-0" role="button">Go to NLP Logs</a>
        </div></div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <div class="card"><div class="card-body">
            <h5 class="card-title">☁️ Application Practice</h5>
            <a href="/challenge/cloud/" class="btn btn-sm z-depth-0" role="button">Go to Application Practice Logs</a>
        </div></div>
    </div>
</div>