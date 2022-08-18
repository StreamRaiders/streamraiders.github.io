---
layout: page
#default-jekyll-theme-midnight
title: Botters
permalink: /botters/
---
##### (Not really in the theme of the website, but still...) The following players have violated the [Guidelines](https://captain.tv/guidelines) by operating multiple accounts through third-party clients in an automated manner (their bot accounts are not disclosed here). They have admitted on multiple occasions to have extensive knowledge about bot operations. They have accused other players of botting to distract the streamer from their own bot accounts and get more rewards. Of course, most of them would deny any such activity.

### Thanks to all players who report botting activity (including factual evidence) to us directly, helping keeping this list up-to-date!

{% if site.data.botters %}

{% assign allbotters = site.data.botters | sort_natural %}

<table id="botters-table">
  <thead>
    <tr>
      <th>Username</th>
    </tr>
  </thead>
{% tablerow botter in allbotters cols:1 %}
  <a href="https://www.streamraiders.com/report/" target="_blank" rel="noopener noreferrer">{{ botter }}</a>
{% endtablerow %}
</table>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
$(document).ready( function () {
  $('#botters-table').DataTable({
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
