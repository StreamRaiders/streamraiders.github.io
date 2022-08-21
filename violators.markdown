---
layout: page
#default-jekyll-theme-midnight
title: Violators
permalink: /violators/
---
##### The following Stream Raiders captains have violated the [Guidelines](https://captain.tv/guidelines) by allowing, supporting, promoting, encouraging or spreading harassment in their communities. Of course, most of them would deny any such activity. Sometimes even going as far as stating the opposite and claiming it's not based on anything factual.
###### If you are as blind as bigheadmikebmx, the reason is "Harassment": specifically bullying and insulting the players as well as prompting other to behave this way.

**P.S.** If you got banned by one of these captains while they were in your favorites and now you have a blank favorite taking up space on your captain selection screen - get in touch, we can help you remove them.

### Thanks to all players who report harassment incidents (including factual evidence) to us directly, helping keeping this list up-to-date!
###### All evidence is double-checked against VODs. If the captain has VODs disabled or paywalled the evidence is assumed valid until proven otherwise.

> [[2 July, 2022]](https://discord.com/channels/500415557800296449/500415558257344514/992978656152535090){:target="_blank"}{:rel="noopener noreferrer"} ctv_kermond: ... calling out specific Captains is a specific no-no - you can use the Reporting function for that!

##### But calling out specific Players is a specific yes-yes, apparently. It is common knowledge that all reports are ignored. You might as well toss a coin into a wishing well for a better effect.

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

<table id="violators-table">
  <thead>
    <tr>
      <th>Captain</th>
    </tr>
  </thead>
{% tablerow violator in allviolators cols:1 %}
  <a href="https://www.streamraiders.com/report/" target="_blank" rel="noopener noreferrer">{{ violator }}</a>
{% endtablerow %}
</table>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
$(document).ready( function () {
  $('#violators-table').DataTable({
    "paging": true,
    "info": false,
    "lengthChange": false,
    "ordering": false,
    "pageLength": 5,
    "pagingType": "full"
  });
} );
</script>
<style>
  .dataTables_wrapper .dataTables_paginate .paginate_button
  {
    min-width: 0.2em !important;
    padding:.1em .1em !important;
  }
  .dataTables_wrapper {
    width: 25%;
  }
</style>

{% endif %}
