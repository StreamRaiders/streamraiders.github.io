---
layout: page
#default-jekyll-theme-midnight
title: Botters
permalink: /botters/
---

###### Not really in the theme of the website, but still...
# The following players have violated the [Guidelines](https://captain.tv/guidelines) by operating multiple accounts through third-party clients in an automated manner.
#### They have admitted on multiple occasions to have extensive knowledge about bot operations.
###### Of course, most of them would deny any such activity.

{% if site.data.botters %}

{% assign allbotters = site.data.botters | sort_natural %}

<table>
{% tablerow botter in allbotters cols:5 %}
  {{ botter }}
{% endtablerow %}
</table>

{% endif %}
