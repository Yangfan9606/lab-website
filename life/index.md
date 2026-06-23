---
title: Lab Life
---

{% comment %}
  Full "Lab Life" listing. Reached from the Blog page's "More" button.
  No `nav:` block on purpose, so it stays out of the top navigation.
  Items come from the `_life/` collection (admin -> "Lab Life").
{% endcomment %}

# {% include icon.html icon="fa-solid fa-mug-hot" %}{{ site.data.content.blog.life_heading | default: "Lab Life" }}

{{ site.data.content.blog.life_intro }}

{% include section.html %}

{% assign items = site.life | sort: "order" %}
{% for item in items %}
  {%
    include life-card.html
    image=item.image
    title=item.title
    subtitle=item.subtitle
    link=item.url
  %}
{% endfor %}

{% include section.html %}

<p class="center">
  <a href="{{ '/blog/' | relative_url }}">
    {% include icon.html icon="fa-solid fa-arrow-left" %}
    Back to Blog
  </a>
</p>
