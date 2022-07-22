---
layout: page
#default-jekyll-theme-midnight
title: Violators
permalink: /violators/
---

# The following captains have violated the [Guidelines](https://captain.tv/guidelines) by allowing, supporting, promoting, encouraging or spreading toxicity and harassment in their communities.
###### Of course, most of them would deny any such activity. Sometimes even going as far as stating the opposite and claiming it's not based on anything factual.

> [2 July, 2022] ctv_kermond: ... calling out specific Captains is a specific no-no - you can use the Reporting function for that!

##### But calling out specific Players is a specific yes-yes, apparently.
##### It is common knowledge that all reports are ignored. You might as well toss a coin into a wishing well for a better effect.

{% if site.data.names and site.data.violators %}

{% for violator in site.data.violators %}
  {%- assign my_key = violator | string -%}
  {% if site.data.names contains my_key %}
    {%- assign name = site.data.names[my_key] -%}
  {% else %}
    {%- assign name = "MISSING NAME, SORRY" -%}
  {% endif %}
  {% capture tmp %}{{ tmp }}#{{ name }}{% endcapture %}
{% endfor %}

{% assign allviolators = tmp | remove_first: '#' | split: '#' | sort_natural %}

<table>
{% tablerow violator in allviolators cols:5 %}
  <a href="https://twitch.tv/{{ violator }}">{{ violator }}</a>
{% endtablerow %}
</table>

{% endif %}
