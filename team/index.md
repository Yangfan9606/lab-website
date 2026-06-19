---
title: Team
nav:
  order: 3
  tooltip: About our team
---

# {% include icon.html icon="fa-solid fa-users" %}Team

{{ site.data.content.team.intro }}

{% include section.html %}

{% include list.html data="members" component="portrait" filter="role == 'pi'" %}
{% include list.html data="members" component="portrait" filter="role != 'pi'" %}

{% include section.html background="images/background.jpg" dark=true %}

{{ site.data.content.team.band }}

{% include section.html %}

{% capture content %}

{% for photo in site.data.content.team.figures %}
{% include figure.html image=photo %}
{% endfor %}

{% endcapture %}

{% include grid.html style="square" content=content %}
