---
layout: page
#default-jekyll-theme-midnight
title: Botters
permalink: /botters/
---
<div style="display: flex">
<div style="flex: 1">

<h5>(Not really in the theme of the website, but still...) The following players have violated the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> by operating multiple accounts through third-party clients in an automated manner (their bot accounts are not disclosed here). They have admitted on multiple occasions to have extensive knowledge about bot operations. They have accused other players of botting to distract the streamer from their own bot accounts and get more rewards from battles and skins from skinathons. Of course, most of them would deny any such activity.</h5>

<h3>Thanks to all players who report botting activity (including factual evidence) to us directly, helping keeping this list up-to-date!</h3>

</div>
<div style="flex: 0 25%">

{% if site.data.botters %}

{% assign allbotters = site.data.botters | sort_natural %}

<table id="botters-table">
  <thead>
    <tr>
      <th>Username</th>
    </tr>
  </thead>
{% tablerow botter in allbotters cols:1 %}
  <a href="https://docs.google.com/forms/d/e/1FAIpQLScMww5NMZzZLDgQnmrCSlQ-yL_l6qTrBEDxwwOds47_h10-hQ/viewform?entry.493095195=Cheating%2FAutomating%2FExploiting&entry.1613546988={{ botter }}&entry.1606568074=-" target="_blank" rel="noopener noreferrer">{{ botter }}</a>
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
    "pageLength": 4,
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
</style>

{% endif %}

</div>
</div>

<h6><strong>How to detect bot accounts:</strong> Accounts which place units in loyalty chest battles (loyalty skin chest, loyalty gold chest, loyalty token chest, loyalty scroll chest, boss chest, superboss chest) without having gold loyalty with the captain are bot accounts. Real players always reach gold loyalty at the start of each event first to maximize the loot since the number of loyalty chests per event is limited and the loot obtained is heavily determined by the color of the loyalty swords.</h6>
<h6>Yes, this is not a good way to tell if someone is a bot, but it is much better than whatever nonsence many players and captains are employing using assumptions, suspicions, lack of game knowledge or even straight up name shaming.</h6>
