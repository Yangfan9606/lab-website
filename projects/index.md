---
title: Projects
nav:
  order: 2
  tooltip: Software, datasets, and more
---

# {% include icon.html icon="fa-solid fa-wrench" %}Projects

{{ site.data.content.projects.intro }}

{% include tags.html tags="publication, resource, website" %}

{% include search-info.html %}

{% include section.html %}

{% comment %}
  Each project has an "Order" number (admin -> Projects). Cards are sorted
  by it within each section, smallest first, so you can pin/fix the order.
  Items left blank float to the front (give them a number to place them).
{% endcomment %}

## Featured

{% assign featured = site.projects | where: "group", "featured" | sort: "order" %}
{% for p in featured %}
  {%
    include card.html
    image=p.image
    title=p.title
    subtitle=p.subtitle
    link=p.link
    description=p.description
    repo=p.repo
    tags=p.tags
    tooltip=p.tooltip
  %}
{% endfor %}

{% include section.html %}

## More

{% assign more = site.projects | where_exp: "item", "item.group != 'featured'" | sort: "order" %}
{% for p in more %}
  {%
    include card.html
    image=p.image
    title=p.title
    subtitle=p.subtitle
    link=p.link
    description=p.description
    repo=p.repo
    tags=p.tags
    tooltip=p.tooltip
    style="small"
  %}
{% endfor %}
