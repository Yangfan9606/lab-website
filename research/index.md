---
title: Research
nav:
  order: 1
  tooltip: Published works
---

# {% include icon.html icon="fa-solid fa-microscope" %}Research

{{ site.data.content.research.intro }}

{% include section.html %}

## {{ site.data.content.research.highlighted_heading }}

{% for paper in site.data.content.research.highlighted %}
{% include citation.html lookup=paper style="rich" %}
{% endfor %}

{% include section.html %}

## {{ site.data.content.research.all_heading }}

{% include search-box.html %}

{% include search-info.html %}

{% include list.html data="citations" component="citation" style="rich" %}

{% if site.data.content.research.videos.size > 0 %}

{% include section.html %}

## {{ site.data.content.research.videos_heading }}

{% for v in site.data.content.research.videos %}
  {% assign url = v.url %}
  {% if url contains "youtu.be/" %}
    {% assign vid = url | split: "youtu.be/" | last | split: "?" | first %}
  {% elsif url contains "v=" %}
    {% assign vid = url | split: "v=" | last | split: "&" | first %}
  {% else %}
    {% assign vid = url | split: "/" | last | split: "?" | first %}
  {% endif %}
  <div style="max-width: 700px; margin: 0 auto 30px;">
    <div style="position: relative; width: 100%; aspect-ratio: 16 / 9;">
      <iframe
        src="https://www.youtube.com/embed/{{ vid }}"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0; border-radius: var(--rounded); box-shadow: var(--shadow);"
        loading="lazy"
        allowfullscreen
        title="{{ v.title | default: 'video' }}"
      ></iframe>
    </div>
    {% if v.title %}<p>{{ v.title }}</p>{% endif %}
  </div>
{% endfor %}

{% endif %}
