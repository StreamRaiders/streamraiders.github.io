---
layout: page
#default-jekyll-theme-midnight
title: Ratings
permalink: /ratings/
---
<head>
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.11.5/css/jquery.dataTables.min.css"/>
</head>

# Since March 24, 2022 (Pixel Shogunate event)

{% assign today = site.time | date: '%s' %}
{% assign start = '24-03-2022 11:00:00' | date: '%s' %}
{% assign daysSince = today | minus: start | divided_by: 60 | divided_by: 60 | divided_by: 24 %}

{% if site.data.lames and site.data.names and site.data.violators %}

<table id="ratings-table">
  <thead>
    <tr>
      <th>Captain</th>
      <th>Battles<br/>on record</th>
      <th title="Each action performed with over 5 minutes delay is a -1 rating. Each perfectly completed battle is a +0.01 rating.">Reliability<br/>rating</th>
      <th title="Higher rating means faster event tiers!">Effective<br/>rating</th>
    </tr>
  </thead>
  {% for entry in site.data.lames %}
  {% assign my_key = entry[0] | string %}
  {% unless site.data.violators contains my_key %}
  <tr>
    {% assign battles = entry[1].c | plus: entry[1].l %}
    {% assign rating = entry[1].c | times: 1.0 | divided_by: 100 | minus: entry[1].l %}
    {% assign battlesPerDay = battles | divided_by: daysSince %}
    {% assign factor = rating | divided_by: battles | times: 100.0 %}
    {% assign effective = factor | times: battlesPerDay | round: 2 %}
    <td> {% if site.data.names contains my_key %} {{ site.data.names[my_key] }} {% else %} <b>MISSING NAME, SORRY</b> {% endif %} </td><td> {{ battles }} </td><td> {{ rating }} </td><td> {{ effective }} </td>
  </tr>
  {% endunless %}
  {% endfor %}
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
    "order": [[ 2, "desc" ], [ 1, "asc" ], [ 3, "desc" ]]
  });
} );
</script>

{% endif %}