---
layout: page
title: Violators
description: Stream Raiders captains that violate the Guidelines by harassing the players
permalink: /violators/
---
<div style="display: flex">
<div style="flex: 1">

<p>The following Stream Raiders captains have violated the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> by allowing, supporting, promoting, encouraging or spreading harassment in their communities. Of course, most of them would deny any such activity. Sometimes even going as far as stating the opposite and claiming it's not based on anything factual or lacking any rhyme or reason.</p>

To all the captains that assume people are bots and state "If you are not - please say so in chat":
<blockquote><p>AmicuNoa: ...creating an unpleasant situation by forcing an unwanted contact ... is harassment</p></blockquote>

<p>The harassment will doubtfully stop spreading faster than COVID19 until CTV start to actually enforce their own Guidelines. In other words, never.</p>

<!-- <p><strong>P.S.</strong> If you got banned by one of these captains while they were in your favorites and now you have a blank favorite taking up space on your captain selection screen - get in touch, we can help you remove them without waiting an eternity for a reply from support and without using any 3rd party applications.</p> -->

<p style="font-size:larger"><b>Thanks to all players who report harassment incidents (including factual evidence) to us directly, helping keeping this list up-to-date!</b></p>
<p>All evidence is double-checked against VODs. If the captain has VODs disabled or paywalled the evidence is assumed valid until proven otherwise.</p>

<blockquote><p><a href="https://discord.com/channels/500415557800296449/500415558257344514/992978656152535090" target="_blank" rel="noopener noreferrer">[2 July, 2022]</a> ctv_kermond: ... calling out specific Captains is a specific no-no - you can use the Reporting function for that!</p></blockquote>

<p>But calling out specific Players is a specific yes-yes, apparently. It is common knowledge that all reports are ignored. You might as well toss a coin into a wishing well for a better effect.</p>

</div>
<div style="flex: 0 25%">

{% if site.data.names and site.data.violators %}

{% for violator in site.data.violators %}
  {%- assign my_key = violator | string -%}
  {% if site.data.names contains my_key %}
    {%- assign name = site.data.names[my_key] -%}
  {% else %}
    {%- assign name = "MISSING NAME, SORRY(" | append: my_key | append: ")" -%}
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
  <a href="https://docs.google.com/forms/d/e/1FAIpQLScMww5NMZzZLDgQnmrCSlQ-yL_l6qTrBEDxwwOds47_h10-hQ/viewform?entry.493095195=Harassment&entry.1613546988={{ violator }}&entry.1606568074=-" target="_blank" rel="noopener noreferrer">{{ violator }}</a>
{% endtablerow %}
</table>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
$(document).ready( function () {
  $('#violators-table').DataTable({
    "paging": false,
    "info": false,
    "ordering": false,
    "scrollY": 425,
    "scrollCollapse": true
  });
} );
</script>
<style>
  .dataTables_wrapper .dataTables_paginate .paginate_button
  {
    min-width: 0.2em !important;
    padding:.1em .1em !important;
  }
</style>

{% endif %}

</div>
