---
---

# {{ site.data.content.home.title }}

{{ site.data.content.home.intro }}

{%
  include button.html
  type="docs"
  link="https://greene-lab.gitbook.io/lab-website-template-docs"
%}
{%
  include button.html
  type="github"
  text="On GitHub"
  link="greenelab/lab-website-template"
%}

{% include section.html %}

## Highlights

{% capture text %}

{{ site.data.content.home.feature1_text }}

{%
  include button.html
  link="research"
  text=site.data.content.home.feature1_button
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %}

{%
  include feature.html
  image=site.data.content.home.feature1_image
  link="research"
  title=site.data.content.home.feature1_title
  text=text
%}

{% capture text %}

{{ site.data.content.home.feature2_text }}

{%
  include button.html
  link="projects"
  text=site.data.content.home.feature2_button
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %}

{%
  include feature.html
  image=site.data.content.home.feature2_image
  link="projects"
  title=site.data.content.home.feature2_title
  flip=true
  style="bare"
  text=text
%}

{% capture text %}

{{ site.data.content.home.feature3_text }}

{%
  include button.html
  link="team"
  text=site.data.content.home.feature3_button
  icon="fa-solid fa-arrow-right"
  flip=true
  style="bare"
%}

{% endcapture %}

{%
  include feature.html
  image=site.data.content.home.feature3_image
  link="team"
  title=site.data.content.home.feature3_title
  text=text
%}

{% include section.html %}

{% comment %} Same photo wall as the Team page (one row + More). Edited under Pages -> Team. {% endcomment %}
{% assign pmax = site.data.content.team.photos_max | plus: 0 %}
{%
  include photo-row.html
  photos=site.data.content.team.figures
  limit=pmax
  size=site.data.content.team.photos_size
  id="home"
%}

{% if site.data.content.team.figures.size > pmax %}
{%
  include button.html
  link="photos"
  text="More photos"
  icon="fa-solid fa-arrow-right"
  flip=true
%}
{% endif %}
