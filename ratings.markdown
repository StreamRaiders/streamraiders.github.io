---
layout: page
title: Ratings
description: How reliable are Stream Raiders captains at running their battles on time?
permalink: /ratings/
---
#### Since March 24, 2022 (Pixel Shogunate event), last update: see Main page.

###### Captains promoting this website to their community by sharing the link during an event will get a shoutout here for the duration of the next event. [Violators]({%link violators.markdown%}){:target="_blank"}{:rel="noopener noreferrer"} are obviously not eligible.

{%- assign today = site.time | date: '%s' -%}
{%- assign start = '24-03-2022 11:00:00' | date: '%s' -%}
{%- assign daysSince = today | minus: start | divided_by: 60 | divided_by: 60 | divided_by: 24 -%}

{% if site.data.lames and site.data.names and site.data.violators %}

<table id="ratings-table">
  <thead>
    <tr>
      <th>Captain</th>
      <th title="Each action performed with over 5 minutes delay is a -1 rating. Each perfectly completed battle is a +0.01 rating.">Reliability<br/>rating</th>
      <th title="Higher rating means faster event tiers!">Effective<br/>rating</th>
      <th>Efficiency</th>
    </tr>
  </thead>
  {%- for entry in site.data.lames -%}
  {%- assign my_key = entry[0] | string -%}
  {%- assign battles = entry[1].c | plus: entry[1].l -%}
  {% unless site.data.violators contains my_key or battles < daysSince %}
  <tr>
    {%- assign rating = entry[1].c | times: 1.0 | divided_by: 100 | minus: entry[1].l -%}
    {%- assign effective = entry[1].c | minus: entry[1].l | times: 1.0 | divided_by: daysSince | round: 2 -%}
    {%- assign efficiency = entry[1].c | times: 100.0 | divided_by: battles | round: 2 -%}
    <td>{%- if site.data.names contains my_key -%}<a href="https://twitch.tv/{{ site.data.names[my_key] }}" target="_blank" rel="noopener noreferrer" title="Battles on record: {{ battles }}">{{ site.data.names[my_key] }}</a>{%- else -%}<b>MISSING NAME, SORRY({{-my_key-}})</b>{%- endif -%}</td><td>{{ rating }}</td><td>{{ effective }}</td><td>{{ efficiency }}%</td></tr>
  {%- endunless -%}
  {%- endfor %}
</table>

###### Unable to find the captain you are looking for? Check that they are not a [Violator]({%link violators.markdown%}){:target="_blank"}{:rel="noopener noreferrer"}

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
$(document).ready( function () {
  $('#ratings-table').DataTable({
    "paging": false,
    "scrollY": 300,
    "scrollCollapse": true,
    "info": false,
    "deferRender": false,
    "autoWidth": false,
    "order": [[ 1, "desc" ], [ 2, "desc" ], [ 3, "desc"]],
    "columnDefs": [{"width": "50px", "searchable": false, "orderSequence": [ "desc", "asc" ], "targets": [ -1, -2, -3 ]}]
  });
} );
</script>

{% endif %}
