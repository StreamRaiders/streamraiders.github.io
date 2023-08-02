---
layout: page
title: Botters
exclude: true
description: Streamraiders Stream Raiders bots
permalink: /botters/
---
<style>
  details {
    border: solid 1px gray;
    padding-left: 10px;
    border-radius: 10px;
    padding-right: 10px;
    padding-top: 5px;
    padding-bottom: 5px;
    user-select: none;
    text-align: initial;
  }
  .dataTables_wrapper .dataTables_paginate .paginate_button
  {
    min-width: 0.2em !important;
    padding:.1em .1em !important;
  }
</style>

<div style="display:flex">
<div style="flex:1; margin-right:10pt">

<p style="text-align:justify">The following players have violated the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> by operating multiple accounts through third-party clients in an automated manner. They have admitted on multiple occasions to have extensive knowledge about bot operations. They have accused other players of botting to deceive the streamer and distract from their own bot accounts to get more rewards from battles and skins from skinathons. Of course, most of them would deny any such activity. <a href="https://twitter.com/Vincent_Ntp/status/1640960446898515968" target="_blank" rel="noopener noreferrer">Some people</a> even go as far as to accuse us of defamation without providing any evidence to support their claim or merely moving a finger to find the obvious evidence supporting our classification. :unamused:</p>

<details>
	<summary>Example lies</summary>
	<details>
		<summary>Tzepiboo</summary>
		<p style="font-size:smaller">In Treecle's channel on 25/09/2022:</p><blockquote>Yeah the bots like to inflate treecle's enemy count and then abandon her for loyalty chests</blockquote>
		<p style="font-size:smaller">In ShanChan's channel on 24/10/2022:</p><blockquote>They even had the nerve to claim I have extensive knowledge of botting and brag about it, which I don't</blockquote>
	</details>
	<details>
		<summary>L0ne_Hermit</summary>
    <p style="font-size:smaller">In byeol_rl's channel on 17/07/2022:</p><blockquote>Omg why the bots came after i placed my unit :rofl:</blockquote>
    <p style="font-size:smaller">In Teddiosg's channel on 19/07/2022:</p><blockquote>The bot problem</blockquote>
    <p style="font-size:smaller">In xsubcube's channel on 28/07/2022:</p><blockquote>i think the botter is here also</blockquote>
    <p style="font-size:smaller">In byeol_rl's channel on 30/07/2022:</p><blockquote>wah these bot armies</blockquote>
    <p style="font-size:smaller">In Teddiosg's channel on 03/02/2023:</p><blockquote>i still dunno why i was in the botter list</blockquote>
	</details>
</details>

<!-- <p style="font-size:larger"><b>Thanks to all players who report botting activity (including factual evidence) to us directly, helping keeping this list up-to-date!</b></p> -->

<h3 style="text-align:center; margin-top:15pt">How to detect bot accounts</h3>
<p style="text-align:justify">Accounts which place units in loyalty chest battles (loyalty skin chest, loyalty gold chest, loyalty token chest, loyalty scroll chest, boss chest, superboss chest) without having gold loyalty with the captain are bot accounts. Real players always reach gold loyalty at the start of each event first to maximize the loot since the number of loyalty chests per event is limited and the loot obtained is heavily determined by the color of the loyalty swords.</p>
<p style="font-size:smaller; text-align:justify">Yes, this is not a good way to tell if someone is a bot, but it is much better than whatever nonsence many players and captains are employing using assumptions, suspicions, lack of game knowledge (i.e., suffering from the <a href="https://en.wikipedia.org/wiki/Dunning-Kruger_effect" target="_blank" rel="noopener noreferrer">Dunning–Kruger effect</a>) or even straight up name shaming, thereby harassing the players, <a href="/violators/" rel="noopener noreferrer">violating</a> the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a>.</p>

</div>
<input class="tab-shifter" id="tab-shifter" type="checkbox" style="opacity:0; position:absolute; right:0px; top:25%;"  />
<label for="tab-shifter" style="position:absolute; right:0px; top:25%; z-index:1; cursor:pointer; font-size:smaller; text-align:center; writing-mode:vertical-lr; user-select:none;">Bot accounts</label>
<div class="shifter" style="flex:0 30%; position:relative; overflow:hidden">
<div class="main-content" style="width:100%">

{%- if site.data.botters -%}
{% assign allbotters = site.data.botters | sort_natural %}
<table id="botters-table">
  <thead>
    <tr>
      <th>Username</th>
    </tr>
  </thead>
{%- for botter in allbotters %}
  <tr><td><a href="https://docs.google.com/forms/d/e/1FAIpQLScMww5NMZzZLDgQnmrCSlQ-yL_l6qTrBEDxwwOds47_h10-hQ/viewform?entry.493095195=Cheating%2FAutomating%2FExploiting&entry.1613546988={{ botter }}&entry.1606568074=-" target="_blank" rel="noopener noreferrer">{{ botter }}</a></td></tr>
{%- endfor %}
</table>

{%- endif %}
</div>
<div class="overlay-content" style="position:absolute; z-index:1; transition:0.6s; top:0%; left:100%; background:#fff; width:100%">

<p style="font-size:x-small; text-align:justify">We offered CTV advanced bot detection tools but instead got counteroffered with a read-only access to the players database without any NDA restrictions under the premise that they could not care less about enforcing the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> at the moment.</p>
<p style="font-size:x-small; text-align:justify">Below is a sample of confirmed bot accounts. These aren't even trying to behave like humans. If you see your name here you should request a refund from your bot's lousy developer.</p>

{% if site.data.bots -%}

<table id="bots-table">
  <thead>
    <tr>
      <th>Username</th>
    </tr>
  </thead>
{%- assign totalShown = 0 -%}
{%- assign cutoffTS = 'today' | date:'%s' | minus:3456000 -%}
{%- for bot in site.data.bots -%}
  {%- assign shouldShow = false -%}
  {%- for entry in bot[1].activity -%}
    {%- assign activityStart = entry[0] | date:'%s' | plus:0 -%}
    {%- assign activityEnd = entry[1] | date:'%s' | plus:0 -%}
    {%- comment -%}
    Workarounds for recorded intervals of 7 or more days
    {%- endcomment -%}
    {%- if activityStart >= 1658448000 and activityStart <= 1659139200 and activityEnd >= 1658448000 and activityEnd <= 1659139200 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 1-->
    {%- elsif activityStart >= 1660867200 and activityStart <= 1661558400 and activityEnd >= 1660867200 and activityEnd <= 1661558400 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 2-->
    {%- elsif activityStart >= 1662076800 and activityStart <= 1662768000 and activityEnd >= 1662076800 and activityEnd <= 1662768000 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 3-->
    {%- elsif activityStart >= 1665705600 and activityStart <= 1666396800 and activityEnd >= 1665705600 and activityEnd <= 1666396800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 4-->
    {%- elsif activityStart >= 1666915200 and activityStart <= 1667606400 and activityEnd >= 1666915200 and activityEnd <= 1667606400 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 5-->
    {%- elsif activityStart >= 1667520000 and activityStart <= 1668211200 and activityEnd >= 1667520000 and activityEnd <= 1668211200 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 6-->
    {%- elsif activityStart >= 1668729600 and activityStart <= 1669420800 and activityEnd >= 1668729600 and activityEnd <= 1669420800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 7-->
    {%- elsif activityStart >= 1671667200 and activityStart <= 1673049600 and activityEnd >= 1671667200 and activityEnd <= 1673049600 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 8-->
    {%- elsif activityStart >= 1674777600 and activityStart <= 1675468800 and activityEnd >= 1674777600 and activityEnd <= 1675468800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 9-->
    {%- elsif activityStart >= 1677196800 and activityStart <= 1677888000 and activityEnd >= 1677196800 and activityEnd <= 1677888000 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 10-->
    {%- elsif activityStart >= 1677801600 and activityStart <= 1678492800 and activityEnd >= 1677801600 and activityEnd <= 1678492800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 11-->
    {%- elsif activityStart >= 1679529600 and activityStart <= 1680307200 and activityEnd >= 1679529600 and activityEnd <= 1680307200 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 12-->
    {%- elsif activityStart >= 1682035200 and activityStart <= 1682726400 and activityEnd >= 1682035200 and activityEnd <= 1682726400 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 13-->
    {%- elsif activityStart >= 1684454400 and activityStart <= 1685232000 and activityEnd >= 1684454400 and activityEnd <= 1685232000 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 14-->
    {%- elsif activityStart >= 1686787200 and activityStart <= 1687564800 and activityEnd >= 1686787200 and activityEnd <= 1687564800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 15-->
    {%- elsif activityStart >= 1689120000 and activityStart <= 1689984000 and activityEnd >= 1689120000 and activityEnd <= 1689984000 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} 16-->
    {%- else -%}
      {%- if activityEnd > cutoffTS -%}
        {%- assign shouldShow = true -%}
      {%- endif -%}
    {%- endif -%}
  {%- endfor -%}
  {%- if shouldShow %}
  <tr><td><a href="https://docs.google.com/forms/d/e/1FAIpQLScMww5NMZzZLDgQnmrCSlQ-yL_l6qTrBEDxwwOds47_h10-hQ/viewform?entry.493095195=Cheating%2FAutomating%2FExploiting&entry.1613546988={{ bot[1].userName }}&entry.1606568074=-" target="_blank" rel="noopener noreferrer">{{ bot[1].userName }}</a>
    {%- assign totalShown = totalShown | plus:1 -%}
</td></tr>
  {%- endif -%}
{%- endfor %}
</table>
<!--{{totalShown}}-->

{%- endif %}
</div>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script type="text/javascript">
  (function() {
    let table1 = new DataTable('#botters-table', {
        "info": false,
        "paging": false,
        "ordering": false,
        "scrollY": 425,
        "scrollCollapse": true
    });
    let table2 = new DataTable('#bots-table', {
        "info": false,
        "paging": false,
        "scrollY": 290,
        "orderFixed": [ 0, 'asc' ]
    });
  })();
</script>

</div>
</div>
