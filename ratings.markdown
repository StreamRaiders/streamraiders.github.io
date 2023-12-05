---
layout: page
title: Ratings
description: Best Streamraiders Stream Raiders captains
permalink: /ratings/
---
#### Since March 24, 2022 (Pixel Shogunate event), last update: see Main page.

##### Over **2100** players have used this table to improve their game enjoyment during the last event alone!

###### Captains promoting this website to their community by sharing the link during an event will get a shoutout here for the duration of the next event. [Violators]({%link violators.markdown%}){:rel="noopener noreferrer"} are obviously not eligible.

##### If a reduction of your rating was caused by server issues please e-mail <a href="mailto:support@captain.tv?subject=Battle error">support</a> with a VOD timestamp confirming that to improve your rating!

{%- comment -%}### *MOST RELIABLE CAPTAIN* :hugs:[Treecle](https://www.twitch.tv/treecle){:target="_blank"}:hugs:{%- endcomment -%}

{%- assign start = '24-03-2022 11:00:00' | date: '%s' -%}
{%- assign daysSince = 'today' | date: '%s' | minus: start | divided_by: 60 | divided_by: 60 | divided_by: 24 -%}

{% if site.data.lames and site.data.names %}
{%- assign totalShown = 0 %}

<table id="ratings-table">
  <thead>
    <tr>
      <th>Captain</th>
      <th title="Each action (starting the battle after 'Battle is ready' or granting the rewards after the battle is finished) performed with over 5 minutes delay is a -1 rating. Each perfectly completed battle is a +0.01 rating.">Reliability<br/>rating</th>
      <th title="Higher rating means faster event tiers!">Effective<br/>rating</th>
      <th>Efficiency</th>
    </tr>
  </thead>
  {%- for entry in site.data.lames -%}
  {%- assign my_key = entry[0] | string -%}
  {% unless entry[1].c < daysSince %}
  {%- assign battles = entry[1].c | plus: entry[1].l -%}
  {%- assign totalShown = totalShown | plus:1 %}
  <tr>
    {%- assign rating = entry[1].c | times: 1.0 | divided_by: 100 | minus: entry[1].l -%}
    {%- assign effective = entry[1].c | minus: entry[1].l | times: 1.0 | divided_by: daysSince | round: 2 -%}
    {%- assign efficiency = entry[1].c | times: 100.0 | divided_by: battles | round: 2 -%}
    <td>{%- if site.data.names contains my_key -%}<a href="https://www.twitch.tv/{{ site.data.names[my_key] }}" target="_blank" title="Battles on record: {{ battles }}">{{ site.data.names[my_key] }}</a>{%- else -%}<b>MISSING NAME, SORRY({{-my_key-}})</b>{%- endif -%}</td><td>{{ rating }}</td><td>{{ effective }}</td><td>{{ efficiency }}%</td></tr>
  {%- endunless -%}
  {%- endfor %}
</table>
<!--{{daysSince}}>{{totalShown}}/{{site.data.lames.size}}-->

<style>
  h6 {
    margin-top: 5pt;
  }
</style>

###### Unable to find the captain you are looking for? Check that they are not a [Violator]({%link violators.markdown%}){:rel="noopener noreferrer"}

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
