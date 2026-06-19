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
