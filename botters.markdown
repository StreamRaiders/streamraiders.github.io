---
layout: page
title: Botters
description: Stream Raiders bots and their operators
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
  }
  .dataTables_wrapper .dataTables_paginate .paginate_button
  {
    min-width: 0.2em !important;
    padding:.1em .1em !important;
  }
</style>

<div style="display: flex">
<div style="flex: 1">

<p>The following players have violated the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> by operating multiple accounts through third-party clients in an automated manner. They have admitted on multiple occasions to have extensive knowledge about bot operations. They have accused other players of botting to deceive the streamer and distract from their own bot accounts to get more rewards from battles and skins from skinathons. Of course, most of them would deny any such activity.</p>

<details>
	<summary>Example lies</summary>
	<details>
		<summary>Tzepiboo</summary>
		<p style="font-size:smaller">In Treecle's channel on 25/09/2022:</p><blockquote>Yeah the bots like to inflate treecle's enemy count and then abandon her for loyalty chests</blockquote>
		<p style="font-size:smaller">Later in ShanChan's channel on 24/10/2022:</p><blockquote>They even had the nerve to claim I have extensive knowledge of botting and brag about it, which I don't</blockquote>
	</details>
</details>

<!-- <p style="font-size:larger"><b>Thanks to all players who report botting activity (including factual evidence) to us directly, helping keeping this list up-to-date!</b></p> -->

<details>
	<summary>How to detect bot accounts</summary>
	<p>Accounts which place units in loyalty chest battles (loyalty skin chest, loyalty gold chest, loyalty token chest, loyalty scroll chest, boss chest, superboss chest) without having gold loyalty with the captain are bot accounts. Real players always reach gold loyalty at the start of each event first to maximize the loot since the number of loyalty chests per event is limited and the loot obtained is heavily determined by the color of the loyalty swords.</p>
	<p style="font-size:smaller">Yes, this is not a good way to tell if someone is a bot, but it is much better than whatever nonsence many players and captains are employing using assumptions, suspicions, lack of game knowledge (i.e., suffering from the <a href="https://en.wikipedia.org/wiki/Dunning-Kruger_effect" target="_blank" rel="noopener noreferrer">Dunning–Kruger effect</a>) or even straight up name shaming, thereby harassing the players, <a href="/violators/" target="_blank" rel="noopener noreferrer">violating</a> the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a>.</p>
</details>

</div>
<input class="tab-shifter" id="tab-shifter" type="checkbox" style="opacity: 0; position: absolute; right: 0px; top:25%;"  />
<label for="tab-shifter" style="position: absolute; right: 0px; top:25%; z-index:1; cursor: pointer; font-size: smaller; text-align: center; writing-mode: vertical-lr; user-select: none;">Bot accounts</label>
<div class="shifter" style="flex: 0 30%; position: relative; overflow: hidden">
<div class="main-content" style="width: 100%">

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
<div class="overlay-content" style="position: absolute; z-index: 1; transition: 0.6s; top: 0%; left: 100%; background: #fff; width: 100%">

<p style="font-size:x-small">We offered CTV advanced bot detection tools but instead got counteroffered with a read-only access to the players database without any NDA restrictions under the premise that they could not care less about enforcing the <a href="https://captain.tv/guidelines" target="_blank" rel="noopener noreferrer">Guidelines</a> at the moment.</p>
<p style="font-size:x-small">Below is a sample of confirmed bot accounts. These aren't even trying to behave like humans. If you see your name here you should request a refund from your bot's lousy developer.</p>

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
    {%- assign myTS = entry[1] | date:'%s' | plus:0 -%}
    {%- if myTS > cutoffTS -%}
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
