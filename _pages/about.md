---
layout: about
title: about
permalink: /
# subtitle: <a href='#'>Affiliations</a>. Address. Contacts. Motto. Etc.

profile:
  align: left
  image: vldb_2024.png
  image_circular: false # crops the image to make it circular
  more_info: >
    <p>Salt Lake City, UT </p>

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

# latest_posts:
  # enabled: true
  # scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  # limit: 3 # leave blank to include all the blog posts
---

Hi, I’m Whanhee! I’m a PhD student at the [University of
Utah](https://www.utah.edu/), working with [Prof. Anna
Fariha](https://afariha.github.io/) in the [Utah
DBLab](https://mod.cs.utah.edu/). My research focuses on building database
systems that provide data management interpretability and explainability. I am
particularly interested in data management systems and explainable AI.

I received my B.S. in Computer Science from [Hanyang
University](https://www.hanyang.ac.kr/) and my M.S. in Computer Science from
Hanyang University under [Prof. Yong Suk Choi](http://ai.hanyang.ac.kr/member).
During my studies, I worked in the [AI Lab](https://ai.hanyang.ac.kr/), where I
focused on natural language processing.

---

## News

{% if page.announcements.enabled %}
<div class="announcements-section">
  {% include news.liquid %}
</div>
{% endif %}

---

## Publications

- 📄 **[Data-Semantics-Aware Recommendation of Diverse Pivot Tables](https://arxiv.org/pdf/2507.06171)** 💻 [GitHub](https://github.com/whnhch/SAGE)  
  <span class="pub-tag" style="background-color: var(--sigmod-color)">SIGMOD 2026</span>  

- 📄 **[Title of Paper 2](https://dl.acm.org/doi/pdf/10.14778/3685800.3685861?casa_token=Cqd2dwrRpTgAAAAA:AAeCJJoVOR5XL5eT1N08kjgOlWnBRylzDixtR9Pmo66XFC51fUTNxp8_0s_9gATdsaBAdH3JU0HC9A)** 💻 [GitHub](https://github.com/whnhch/UTOPIA-Automatic-Pivot-Table-Assistant)  
  <span class="pub-tag" style="background-color: var(--vldb-color)">VLDB 2024</span>  
