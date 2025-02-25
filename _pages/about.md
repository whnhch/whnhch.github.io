---
permalink: /
title: "Whanhee Cho"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
#### Name Prnounciation
You can pronounce my name as [ha-ni].
My korean name is 조환희.

### About Me
--- 
I am interested in database management and nautral language processing.
Now, I am a Computer Science PhD student at University of Utah working with Prof. Anna Fariha.

<!-- <section>
  <h2>Latest News</h2>
  <div class="news-wrapper">
    <div class="news-item">New publication: <a href="link-to-paper">Title of Paper</a></div>
  </div>
</section> -->

---

### Publications

{% for year_data in site.data.publications %}
  #### {{ year_data.year }}
  <ul>
  {% for pub in year_data.publications %}
    <li>
      {{ pub.title }}<br/>
      <em>{{ pub.authors }}</em>, <em>{{ pub.venue }}</em>. 
      <a href="{{ pub.link }}" target="_blank">[Link]</a>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
