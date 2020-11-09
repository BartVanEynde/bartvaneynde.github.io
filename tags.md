---
layout: page
title: Tags
#background_style: bg-info
background_image: url('/assets/img/backgrounds/image-from-rawpixel-id-1199650-jpeg.jpg')
# Add a link to the the top menu
menus:
  header:
    title: Tags
    weight: 2

# https://gist.github.com/Phlow/a0e3fa686eb259fe7f76 - list-tags-count.liquid
---

<h2>Tags</h2>

<ul>
{% assign tags_list = site.tags %}
  {% if tags_list.first[0] == null %}
    {% for tag in tags_list %}
      <li><a href="#{{ tag | downcase | downcase | url_escape | strip | replace: ' ', '-' }}">{{ tag | camelcase }} ({{ site.tags[tag].size }})</a></li>
    {% endfor %}
  {% else %}
    {% for tag in tags_list %}

      <li><a href="#{{ tag[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ tag[0] | camelcase }} ( {{ tag[1].size }} )</a></li>
    {% endfor %}
  {% endif %}
{% assign tags_list = nil %}
</ul>





<ul>
{% assign tags_list = site.tags %}
  {% if tags_list.first[0] == null %}
    {% for tag in tags_list limit: 3 %}
      <li><a href="/tags/#{{ tag | downcase | downcase | url_escape | strip | replace: ' ', '-' }}">{{ tag | camelcase }} ({{ site.tags[tag].size }})</a></li>
    {% endfor %}
  {% else %}
    {% for tag in tags_list limit:3 %}
      <li><a href="/tags/#{{ tag[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ tag[0] | camelcase }} ( {{ tag[1].size }} )</a></li>
    {% endfor %}
  {% endif %}
{% assign tags_list = nil %}
</ul>




{% for tag in site.tags %}
  <h3 id="{{ tag[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ tag[0] | camelcase }}</h3>
  <ul>
    {% assign pages_list = tag[1] %}
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