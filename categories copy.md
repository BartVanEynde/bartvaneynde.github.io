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


---

{% assign split_mark = '<|>' %}

{% assign categories = '' %}
{% for category in site.categories %}
  {% assign name = category | first %}
  {% assign categories = categories | append: split_mark  | append: name %}
{% endfor %}

{% assign return = categories
  | remove_first: split_mark
  | split: split_mark
  | sort: self %}

<div class="common-list">
  <ul>
    <li>
      <a href="{{ '/index.html' | relative_url }}">
        All<span>{{ site.posts.size }}</span>
      </a>
    </li>

    {% for key in  site.categories %}
      <li>
        <a href="{{ url }}#h-{{ key }}">
          {{ key }} <span>{{ site.posts | where: field, key | size }}</span>
        </a>
      </li>
    {% endfor %}
  </ul>
</div>