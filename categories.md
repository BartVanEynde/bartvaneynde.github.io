---
layout: page
title: Categories
#background_style: bg-info
background_image: url('assets/img/backgrounds/image-from-rawpixel-id-1199650-jpeg.jpg')
# Add a link to the the top menu
menus:
  header:
    title: Categories
    weight: 2

# https://gist.github.com/Phlow/a0e3fa686eb259fe7f76 - list-categories-count.liquid
---

<h2>Categories</h2>
<ul>
{% assign categories_list = site.categories %}
  {% if categories_list.first[0] == null %}
    {% for category in categories_list %}
      <li><a href="#{{ category | downcase | downcase | url_escape | strip | replace: ' ', '-' }}">{{ category | camelcase }} ({{ site.tags[category].size }})</a></li>
    {% endfor %}
  {% else %}
    {% for category in categories_list %}
      <li><a href="#{{ category[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ category[0] | camelcase }} ({{ category[1].size }})</a></li>
    {% endfor %}
  {% endif %}
{% assign categories_list = nil %}
</ul>

{% for category in site.categories %}
  <h3 id="{{ category[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ category[0] | capitalize }}</h3>
  <ul>
    {% assign pages_list = category[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}