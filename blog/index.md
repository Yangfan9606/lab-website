---
title: Blog
nav:
  order: 4
  tooltip: Musings and miscellany
---

# {% include icon.html icon="fa-solid fa-feather-pointed" %}Blog

{{ site.data.content.blog.intro }}

{% include section.html %}

{% include search-box.html %}

{% comment %}
  Lab Life gallery (cover + title cards) shown right below the search box.
  Items are edited under admin -> "Lab Life"; each opens its own page.
  These use class "life-card" (not "card"), so the search box above does
  NOT filter them — search only affects the blog posts further down.
  Heading text + how many to show are set in _data/content/blog.yaml.
{% endcomment %}
{% assign life_items = site.life | sort: "order" %}
{% if life_items.size > 0 %}
  {% assign lifemax = site.data.content.blog.life_max | default: 3 | plus: 0 %}

  <h2 id="lab-life">{{ site.data.content.blog.life_heading | default: "Lab Life" }}</h2>

  {% for item in life_items limit: lifemax %}
    {%
      include life-card.html
      image=item.image
      title=item.title
      subtitle=item.subtitle
      link=item.url
      style="small"
    %}
  {% endfor %}

  {% if life_items.size > lifemax %}
  <p>
    {%
      include button.html
      link="/life/"
      text="More"
      icon="fa-solid fa-arrow-right"
      flip=true
    %}
  </p>
  {% endif %}
{% endif %}

{% include section.html %}

{% include tags.html tags=site.tags %}

{% include search-info.html %}

{% include list.html data="posts" component="post-excerpt" %}
