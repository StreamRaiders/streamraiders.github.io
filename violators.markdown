---
layout: page
#default-jekyll-theme-midnight
title: Violators
permalink: /violators/
---

# The following captains have violated the [Guidelines](https://captain.tv/guidelines) by allowing, supporting, promoting or spreading toxicity in their communities.
###### Of course, most of them would deny any such activity.

{% if site.data.names and site.data.violators %}

<table>
{% assign shv = site.data.violators | sort %}
{% tablerow violator in shv cols:5 %}
  {% assign my_key = violator | string %}
  {% if site.data.names contains my_key %} {% assign name = site.data.names[my_key] %} {% else %} {% assign name = "MISSING NAME, SORRY" %} {% endif %}
  <a href="https://twitch.tv/{{ name }}"> {{ name }} </a>
{% endtablerow %}
</table>

{% endif %}