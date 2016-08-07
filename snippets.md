---
layout: page
title: "Snippets"
description: "Short thoughts"
header-img: "img/Big_Sur.jpg"
order: 2 
---

{% for post in site.posts reversed %}
    {% if post.article-type == 'short' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}