---
title: "Galleri"
permalink: /galleri/
layout: single
classes: wide
header:
#  overlay_image: /assets/images/utsikt_sjön.jpg
---

<div id="are-gallery">
  {% comment %}
  Visa automatiskt alla bilder i assets/images (förutom SVG), som klickbar gallerivy.
  {% endcomment %}
  {% assign gallery_images = site.static_files | where_exp: "file", "file.path contains '/assets/images/'" %}
  {% assign gallery_images = gallery_images | where_exp: "file", "file.extname != '.svg'" %}
  {% assign gallery_images = gallery_images | sort: "path" %}
  {% for file in gallery_images %}
    <figure class="third">
      <a href="{{ file.path }}">
        <img src="{{ file.path }}" alt="{% capture alt %}{{ file.name | split: '.' | first | replace: '-', ' ' | replace: '_', ' ' }}{% endcapture %}{{ alt }}">
      </a>
      <figcaption>{% capture caption %}{{ file.name | split: '.' | first | replace: '-', ' ' | replace: '_', ' ' }}{% endcapture %}{{ caption }}</figcaption>
    </figure>
  {% endfor %}
</div>
