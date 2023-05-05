---
layout: page
title: Explorer
description: Live Streamraiders Stream Raiders game data
permalink: /explorer/
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
</style>

<noscript style="font-size:larger">This feature requires enabled JavaScript to work!</noscript>

<div id="data">Data is loading, please stand by!</div>

<script type="text/javascript">
(function() {
	const commands = ['banViolators', 'stopHarassment', 'enforceGuidelines', 'fire_ctv_river']
	fetch('https://www.streamraiders.com/api/game/?cn=' + commands[(Math.random() * commands.length) | 0], {method: 'POST'}).then((response) => response.json()).then((data) => {fetch(data.info.dataPath, {method: 'GET'}).then((datafile) => datafile.json()).then((datainfo) => parseData(datainfo.sheets, data.info.clientVersion + ' | ' + data.info.version + ' | ' + data.info.dataVersion, data.info.serverTime)).catch((error) => alert('Postload error: ' + error))}).catch((error) => alert('Preload error: ' + error))
})();
function parseData(dictdata, version, serverTime) {
	const target = document.querySelector("#data");
	target.innerHTML = "";
	const notice = document.createElement("p");
	notice.style.fontSize = "x-large";
	notice.innerHTML = "Note: We do <b>NOT</b> host this data. By staying on this page you are personally datamining using your own browser. If you do not wish to do so - navigate from this page immediately!";
	target.appendChild(notice);
	const information = document.createElement("p");
	information.style.fontSize = "x-small";
	information.style.textAlign = "right";
	information.innerText = "Version: " + version + " Server time: " + serverTime;
	target.appendChild(information);
	const postscript = document.createElement("p");
	postscript.innerHTML = "P.S.: Ctrl+F works best in Chromium-based browsers.<br/>Changes omitted from the published patch notes:<ul><li><b>0.52.0/0.213.0</b>: Removed 'Total participants' number from the captain information during search so that players will not be able to tell, which captain is small or large.</li></ul>";
	target.appendChild(postscript);
	Object.entries(dictdata).forEach(entry => {
		const details = document.createElement("details");
		const summary = document.createElement("summary");
		summary.innerText = entry[0]; // key
		details.appendChild(summary);
		if (typeof entry[1] === "object") {
			parseDictMember(entry[1], details, entry[0])
		}
		else{
			const text = document.createTextNode(entry[1]); // value
			details.appendChild(text);
		}
		target.appendChild(details);
	});
}
function parseDictMember(dictdata, target, element) {
	Object.entries(dictdata).forEach(entry => {
		var text = '"' + entry[0] + '":'
		if (typeof entry[1] === "object") {
			text += '\n' + parseDictLeaf(entry[1])
		}
		else{
			text += ' ' + entry[1]; // value
		}
		const member = document.createElement("p");
		member.innerText = text;
		member.style.whiteSpace = "pre-wrap";
		target.appendChild(member);
	});
}
function parseDictLeaf(dictdata) {
	return Object.entries(dictdata).map(entry => '  ' + entry[0] + ': ' + JSON.stringify(entry[1], null, 2)).join('\n');
}
</script>
