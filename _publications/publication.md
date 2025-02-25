---
layout: default
title: Publications
permalink: /publications/
---
<h1>Publications</h1>

{% for year_data in site.data.publications %}
  <h2>{{ year_data.year }}</h2>
  <ul>
  {% for pub in year_data.publications %}
    <li>
      <strong>{{ pub.title }}</strong> <br/>
      {{ pub.authors }} <br/>
      <em>{{ pub.venue }}</em> <br/>
      <a href="{{ pub.link }}" target="_blank">[Link]</a>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
