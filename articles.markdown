---
layout: page
title: "Articles"
description: "Organizing the collection"
header-img: "img/three_sisters.jpg"
---

[Jekyll]: http://jekyllrb.com/ "Jekyll"
[Jekyll version]: https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll "Github: startbootstrap-clean-blog-jekyll"
[Clean Blog]: http://startbootstrap.com/template-overviews/clean-blog/ "startbootstrap.com"
[Github Pages]: https://pages.github.com/ "pages.github.com"

Hockey Pools Series:

{% comment %} [Part 1]({% post_url 2014-08-23-hockey-pools-part-1 %}) {% endcomment %}

{% for post in site.posts reversed %}
    {% if post.categories contains 'hockey pool' %}
* [{% if post.subtitle %} {{ post.subtitle }} {% else %} {{post.title}} {% endif %}]({{ post.url }})
    {% endif %}
{% endfor %}
