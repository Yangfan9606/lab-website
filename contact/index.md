---
title: Contact
nav:
  order: 5
  tooltip: Email, address, and location
---

# {% include icon.html icon="fa-regular fa-envelope" %}Contact

{{ site.data.content.contact.intro }}

{%
  include button.html
  type="email"
  text=site.data.content.contact.email
  link=site.data.content.contact.email
%}
{%
  include button.html
  type="phone"
  text=site.data.content.contact.phone_text
  link=site.data.content.contact.phone_link
%}
{%
  include button.html
  type="address"
  tooltip=site.data.content.contact.address_tooltip
  link=site.data.content.contact.address_link
%}

{% include section.html %}

{% capture content %}

{% for fig in site.data.content.contact.figures %}
{% include figure.html image=fig.image caption=fig.caption %}
{% endfor %}

{% endcapture %}

{% include grid.html style="square" content=content %}

{% include section.html dark=true %}

{% include cols.html col1=site.data.content.contact.col1 col2=site.data.content.contact.col2 col3=site.data.content.contact.col3 %}
