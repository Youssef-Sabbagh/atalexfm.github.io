---
layout: archive
permalink: /datascience/
title: "Data Science Posts by Category"
categories: [Data Science]
author_profile: true
header:
    image: "/images/lights.JPG"
---

{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}