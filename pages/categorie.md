---
layout: page
title: "Categorie"
meta_title: "Categorie"
subheadline: ""
teaser: ""
permalink: "/categorie/"
---

{% for category in site.categories %}
    {{ category | first }}
    <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

