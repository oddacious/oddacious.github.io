---
layout: page
title: "Articles"
description: "Organizing the collection"
header-img: "img/three_sisters.jpg"
---

Hockey Pools Series:

{% comment %} [Part 1]({% post_url 2014-08-23-hockey-pools-part-1 %}) {% endcomment %}

{% for post in site.posts reversed %}
    {% if post.categories contains 'hockey pool' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}

Basketball:

{% for post in site.posts reversed %}
    {% if post.categories contains 'basketball' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}

Other:

{% for post in site.posts reversed %}
    {% unless post.categories contains 'basketball' or post.categories contains 'hockey pool' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endunless %}
{% endfor %}

