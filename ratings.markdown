---
layout: page
#default-jekyll-theme-midnight
title: Ratings
permalink: /ratings/
---
# Since March 24, 2022 (Pixel Shogunate event)

{%- assign today = site.time | date: '%s' -%}
{%- assign start = '24-03-2022 11:00:00' | date: '%s' -%}
{%- assign daysSince = today | minus: start | divided_by: 60 | divided_by: 60 | divided_by: 24 -%}

{% if site.data.lames and site.data.names and site.data.violators %}

<table id="ratings-table">
  <thead>
    <tr>
      <th>Captain</th>
      <th>Battles<br />on record</th>
      <th title="Each action performed with over 5 minutes delay is a -1 rating. Each perfectly completed battle is a +0.01 rating.">Reliability<br/>rating</th>
      <th title="Higher rating means faster event tiers!">Effective<br/>rating</th>
      <th>Efficiency</th>
    </tr>
  </thead>
  {%- for entry in site.data.lames -%}
  {%- assign my_key = entry[0] | string -%}
  {% unless site.data.violators contains my_key %}
  <tr>
    {%- assign battles = entry[1].c | plus: entry[1].l -%}
    {%- assign rating = entry[1].c | times: 1.0 | divided_by: 100 | minus: entry[1].l -%}
    {%- assign effective3 = entry[1].c | minus: entry[1].l | times: 1.0 | divided_by: daysSince | round: 2 -%}
    {%- assign efficiency = entry[1].c | times: 100.0 | divided_by: battles | round: 2 -%}
    {%- comment-%}
      {%- assign battlesPerDay = battles | times: 1.0 | divided_by: daysSince -%}
      {%- assign effective1 = rating | times: 100.0 | divided_by: daysSince | round: 2 -%}
      {%- assign effective2 = rating | plus: battlesPerDay | round: 2 -%}
    {%- endcomment-%}
    <td>{%- if site.data.names contains my_key -%}<a href="https://twitch.tv/{{ site.data.names[my_key] }}">{{ site.data.names[my_key] }}</a>{%- else -%}<b>MISSING NAME, SORRY</b>{%- endif -%}</td><td>{{ battles }}</td><td>{{ rating }}</td><td>{{ effective3 }}</td><td>{{ efficiency }}%</td></tr>
  {%- endunless -%}
  {%- endfor %}
</table>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
$(document).ready( function () {
  $('#ratings-table').DataTable({
    "paging": false,
    "scrollY": 300,
    "info": false,
    "deferRender": true,
    "order": [[ 3, "desc" ], [ 1, "asc" ], [ 2, "desc" ], [ 4, "desc"]]
  });
} );
</script>

{% endif %}
