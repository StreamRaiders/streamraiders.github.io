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

{%- assign startsList = '2022-07-22|2022-08-19|2022-09-02|2022-10-14|2022-10-28|2022-11-04|2022-11-18|2022-12-22|2023-01-27|2023-02-24|2023-03-03|2023-03-23|2023-04-21|2023-05-19|2023-06-15|2023-07-12' | split: '|' -%}
{%- assign starts = '' | split: '|' -%}
{%- for stamp in startsList -%}
  {%- assign value = stamp | date:'%s' | plus:0 -%}
  {%- assign starts = starts | push:value -%}
{%- endfor -%}

{%- assign endsList = '2022-07-29|2022-08-26|2022-09-09|2022-10-21|2022-11-04|2022-11-11|2022-11-25|2023-01-06|2023-02-03|2023-03-03|2023-03-10|2023-03-31|2023-04-28|2023-05-27|2023-06-23|2023-07-21' | split: '|' -%}
{%- assign ends = '' | split: '|' -%}
{%- for stamp in endsList -%}
  {%- assign value = stamp | date:'%s' | plus:0 -%}
  {%- assign ends = ends | push:value -%}
{%- endfor -%}

<!--{{ starts | inspect }} {{ ends | inspect }}-->
{%- for bot in site.data.bots -%}
  {%- assign shouldShow = false -%}
  {%- for entry in bot[1].activity -%}
    {%- assign activityStart = entry[0] | date:'%s' | plus:0 -%}
    {%- assign activityEnd = entry[1] | date:'%s' | plus:0 -%}
    {%- comment -%}
    Workarounds for recorded intervals of 7 or more days
    {%- endcomment -%}
    {%- if activityStart >= starts[0] and activityStart <= ends[0] and activityEnd >= starts[0] and activityEnd <= ends[0] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 0-->
    {%- elsif activityStart >= starts[1] and activityStart <= ends[1] and activityEnd >= starts[1] and activityEnd <= ends[1] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 1-->
    {%- elsif activityStart >= starts[2] and activityStart <= ends[2] and activityEnd >= starts[2] and activityEnd <= ends[2] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 2-->
    {%- elsif activityStart >= starts[3] and activityStart <= ends[3] and activityEnd >= starts[3] and activityEnd <= ends[3] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 3-->
    {%- elsif activityStart >= starts[4] and activityStart <= ends[4] and activityEnd >= starts[4] and activityEnd <= ends[4] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 4-->
    {%- elsif activityStart >= starts[5] and activityStart <= ends[5] and activityEnd >= starts[5] and activityEnd <= ends[5] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 5-->
    {%- elsif activityStart >= starts[6] and activityStart <= ends[6] and activityEnd >= starts[6] and activityEnd <= ends[6] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 6-->
    {%- elsif activityStart >= starts[7] and activityStart <= ends[7] and activityEnd >= starts[7] and activityEnd <= ends[7] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 7-->
    {%- elsif activityStart >= starts[8] and activityStart <= ends[8] and activityEnd >= starts[8] and activityEnd <= ends[8] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 8-->
    {%- elsif activityStart >= starts[9] and activityStart <= ends[9] and activityEnd >= starts[9] and activityEnd <= ends[9] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 9-->
    {%- elsif activityStart >= starts[10] and activityStart <= ends[10] and activityEnd >= starts[10] and activityEnd <= ends[10] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 10-->
    {%- elsif activityStart >= starts[11] and activityStart <= ends[11] and activityEnd >= starts[11] and activityEnd <= ends[11] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 11-->
    {%- elsif activityStart >= starts[12] and activityStart <= ends[12] and activityEnd >= starts[12] and activityEnd <= ends[12] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 12-->
    {%- elsif activityStart >= starts[13] and activityStart <= ends[13] and activityEnd >= starts[13] and activityEnd <= ends[13] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 13-->
    {%- elsif activityStart >= starts[14] and activityStart <= ends[14] and activityEnd >= starts[14] and activityEnd <= ends[14] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 14-->
    {%- elsif activityStart >= starts[15] and activityStart <= ends[15] and activityEnd >= starts[15] and activityEnd <= ends[15] -%}
      <!--{{ bot[0] }} {{ bot[1].userName }} {{ entry[0] }} {{ entry[1] }} {{ activityStart }} {{ activityEnd }} 15-->
    {%- else -%}
      {%- assign shouldShow = true -%}
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
