---
layout: page
title: "Snippets"
description: "Short thoughts"
header-img: img/barbados.jpg
order: 2 
---

{% for post in site.posts reversed %}
    {% if post.article-type == 'short' %}
* [{% if post.subtitle %}{{ post.subtitle }}{% else %}{{ post.title }}{% endif %} \[{{post.date | date: "%Y-%m-%d"}}\]]({{ post.url }}){:class="articles"} 
    {% endif %}
{% endfor %}
