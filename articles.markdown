---
layout: page
title: "Articles"
description: "Organizing the collection"
header-img: "img/three_sisters.jpg"
order: 1
---

**Goalie evaluation:**

{% for post in site.posts reversed %}
    {% if post.categories contains 'goalies' and post.article-type == 'long' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}

**Hockey Pools Series:**

{% for post in site.posts reversed %}
    {% if post.categories contains 'hockey pool' and post.article-type == 'long' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}

**Basketball:**

{% for post in site.posts reversed %}
    {% if post.categories contains 'basketball' and post.article-type == 'long' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}

**Other:**

{% for post in site.posts reversed %}
    {% if post.article-type == 'long' %}
        {% unless post.categories contains 'basketball' or post.categories contains 'hockey pool' or post.categories contains 'goalies' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
        {% endunless %}
    {% endif %}
{% endfor %}

