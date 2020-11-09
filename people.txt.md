---
layout: page
title: People
permalink: /people/txt/
#background_style: bg-info
background_image: url('assets/img/backgrounds/image-from-rawpixel-id-1199650-jpeg.jpg')
# Add a link to the the top menu
menus:
  header:
    title: People
    weight: 2

# https://gist.github.com/roachhd/ff66af9fd920a15c75a3 - roachhd/README.md
---

<h2>People</h2>

{% for category in site.categories %}
  {% if category[0] contains 'people'  %}
  <ul>
    {% assign pages_list = category[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a>
      </li>
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
  {% endif %}
{% endfor %}





