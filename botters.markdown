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
    {%- if activityStart >= 1658440800 and activityStart <= 1659045600 and activityEnd >= 1658440800 and activityEnd <= 1659045600 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1660860000 and activityStart <= 1661464800 and activityEnd >= 1660860000 and activityEnd <= 1661464800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1662069600 and activityStart <= 1662674400 and activityEnd >= 1662069600 and activityEnd <= 1662674400 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1665698400 and activityStart <= 1666303200 and activityEnd >= 1665698400 and activityEnd <= 1666303200 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1666908000 and activityStart <= 1667516400 and activityEnd >= 1666908000 and activityEnd <= 1667516400 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1667516400 and activityStart <= 1668121200 and activityEnd >= 1667516400 and activityEnd <= 1668121200 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1668726000 and activityStart <= 1669330800 and activityEnd >= 1668726000 and activityEnd <= 1669330800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1671663600 and activityStart <= 1672959600 and activityEnd >= 1671663600 and activityEnd <= 1672959600 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1674774000 and activityStart <= 1675378800 and activityEnd >= 1674774000 and activityEnd <= 1675378800 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
    {%- elsif activityStart >= 1679526000 and activityStart <= 1680213600 and activityEnd >= 1679526000 and activityEnd <= 1680213600 -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }}-->
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
