---
title: Team
nav:
  order: 3
  tooltip: About our team
---

# {% include icon.html icon="fa-solid fa-users" %}Team

{{ site.data.content.team.intro }}

{% include section.html %}

{% comment %} Photo wall, moved to the top. Edited under Pages -> Team. {% endcomment %}
{% capture content %}

{% for photo in site.data.content.team.figures %}
{% include figure.html image=photo %}
{% endfor %}

{% endcapture %}

{% include grid.html style="square" content=content %}

{% include section.html %}

{% comment %}
  Team is grouped into sections by role, in this fixed order (PI/Leader first).
  To add or reorder a role: edit this list AND _data/types.yaml (icon + label)
  AND the Role dropdown in admin/config.yml. Empty groups are skipped.
{% endcomment %}
{% assign role_order = "principal-investigator,co-pi,research-scientist,postdoc,phd,masters,undergrad,programmer,lab-manager,visiting,rotation,alumni" | split: "," %}

{% for role in role_order %}
  {% assign group = site.members | where: "role", role | sort: "name" %}
  {% if group.size > 0 %}

## {{ site.data.types[role].description | default: role }}

{% for member in group %}{% include portrait.html lookup=member.slug %}{% endfor %}

  {% endif %}
{% endfor %}

{% include section.html background="images/background.jpg" dark=true %}

{{ site.data.content.team.band }}
