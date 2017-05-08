---
layout: page
title: Group Expertise
excerpt: "Group Members"
modified: 2014-08-08T19:44:38.564948-04:00
---




<script src="src/d3.v4.min.js"></script>
<script src="src/viz.v1.1.0.min.js"></script>


<script>

var data = [
['Evan','QMC/Model Hamiltonians',1]
,['Chris','QMC/Model Hamiltonians',1]
,['Cedric','QMC/Model Hamiltonians',1]
,['Evgeny','QMC/Model Hamiltonians',1]
,['Swagata','QMC/Model Hamiltonians',1]
,['Carla','QMC/Model Hamiltonians',1]
,['Evan','DMFT',1]
,['Chris','DMFT',1]
,['Cedric','DMFT',1]
,['Swagata','DMFT',1]
,['Evgeny','DMFT',1]
,['Francois','DMFT',1]
,['Duncan','Quantum Chemistry/Molecules',1]
,['Vincent','Quantum Chemistry/Molecules',1]
,['George','Quantum Chemistry/Molecules',1]
,['Carla','Quantum Chemistry/Molecules',1]
,['Mohamed Ali','Quantum Chemistry/Molecules',1]
,['Edouardo','Quantum Chemistry/Molecules',1]
,['Duncan','Spectroscopy',1]
,['Francois','Spectroscopy',1]
,['Swagata','Spectroscopy',1]
,['Cedric','Spectroscopy',1]
,['Mohamed Ali','Spectroscopy',1]
,['Cono', 'Transport', 1]
,['Vincent', 'Transport', 1]
,['Francesco', 'Transport', 1]
,['Nicola', 'Transport', 1]
,['Cedric', 'Superconductivity',1]
,['Swagata', 'Superconductivity',1]
,['Chris', 'Superconductivity',1]
,['Francois', 'Superconductivity',1]
,['Vincent', 'Superconductivity',1]
,['Evgeny', 'Superconductivity',1]
,['George', 'Superconductivity',1]
,['QMC/Model Hamiltonians', 'Evan', 1 ]
,['QMC/Model Hamiltonians', 'Chris', 1 ]
,['QMC/Model Hamiltonians', 'Cedric', 1 ]
,['QMC/Model Hamiltonians', 'Evgeny', 1]
,['QMC/Model Hamiltonians', 'Swagata', 1]
,['QMC/Model Hamiltonians', 'Carla', 1]
,['DMFT', 'Evan', 1 ]
,['DMFT', 'Chris', 1 ]
,['DMFT', 'Cedric', 1 ]
,['DMFT', 'Swagata', 1]
,['DMFT', 'Evgeny', 1]
,['DMFT', 'Francois', 1]
,['Quantum Chemistry/Molecules', 'Duncan', 1]
,['Quantum Chemistry/Molecules' , 'Vincent', 1]
,['Quantum Chemistry/Molecules' , 'George', 1]
,['Quantum Chemistry/Molecules' , 'Carla', 1]
,['Quantum Chemistry/Molecules', 'Mohamed Ali', 1]
,['Quantum Chemistry/Molecules', 'Edouardo', 1]
,['Spectroscopy', 'Duncan', 1]
,['Spectroscopy', 'Francois', 1]
,['Spectroscopy', 'Swagata', 1]
,['Spectroscopy', 'Cedric', 1]
,['Spectroscopy', 'Mohamed Ali', 1]
,['Transport', 'Cono', 1]
,['Transport', 'Vincent', 1]
,['Transport', 'Francesco', 1]
,['Transport', 'Nicola', 1]
,['Superconductivity', 'Cedric', 1]
,['Superconductivity', 'Swagata', 1]
,['Superconductivity', 'Chris', 1]
,['Superconductivity', 'Francois', 1]
,['Superconductivity', 'Vincent', 1]
,['Superconductivity', 'Evgeny', 1]
,['Superconductivity', 'George', 1]
];
/*
var data = {['Evan','DMFT',1]
,['Evan','QMC',1]
,['Chris','QMC',1]
,['Chris','DMFT',1]
,['Cedric','DMFT',1]
,['Cedric','QMC',1]
,['Duncan','RIXS',1]
,['QMC', 'Evan', 1 ]
,['QMC', 'Chris', 1 ]
,['QMC', 'Cedric', 1 ]
,['DMFT', 'Evan', 1 ]
,['DMFT', 'Chris', 1 ]
,['DMFT', 'Cedric', 1 ]
}*/

var colors = {"Evan":         "#da4480"
,"Chris":    "#5ab449"
,"Cedric":    "#7f5acd"
,"Duncan":        "#aab740"
, "Cono":   "#ce58c0"
, "Vincent":    "#50a26e"
, "George":   "#d1434b"
, "Edouardo": "#45c0bc"
, "Max": "#ce5929"
, "Francois": "#4e7bda"
, "Francesco": "#d49d3c"
, "Nicola": "#6660a3"
, "Mohamed Ali": "#7b853c"
, "Evgeny": "#b58dde"
, "Swagata": "#97622e"
, "DMFT": "#609dd6"
, "QMC/Model Hamiltonians":"#e29074"
, "Superconductivity":  "#9c4b88"
, "Quantum Chemistry/Molecules":  "#ab505f"
, "Transport": "#dc85b6"
, "Spectroscopy": "#b58dde"
};

/*
var colors = {
"Evan":         "#da4480"
,"Chris":    "#5ab449"
,"Cedric":    "#7f5acd"
,"Duncan":        "#aab740"
,"DMFT": "#ce58c0"
,"QMC":        "#50a26e"
};*/


var sortOrder =[
"Evan"
,"Chris"
,"Cedric"
,"Duncan"
, "Cono"
, "Vincent"
, "George"
, "Edouardo"
, "Max"
, "Francois"
, "Francesco"
, "Nicola"
, "Mohamed Ali"
, "Evgeny"
, "Swagata"
, "DMFT"
, "QMC/Model Hamiltonians"
, "Superconductivity"
, "Quantum Chemistry/Molecules"
, "Transport"
, "Spectroscopy"
];

/*
var sortOrder =[
"Evan"
,"Chris"
,"Cedric"
,"Duncan"
, "DMFT"
, "QMC"
,"RIXS"
];
*/
function sort(a,b){ return d3.ascending(sortOrder.indexOf(a),sortOrder.indexOf(b)); }

var ch = viz.ch().data(data)
      .padding(0.01)
      .sort(sort)
	  .innerRadius(430)
	  .outerRadius(450)
	  .duration(1000)
	  .chordOpacity(0.3)
	  .labelPadding(.03)
      .fill(function(d){ return colors[d];});

var width=1200, height=1100;

var svg = d3.select("body").append("svg").attr("height",height).attr("width",width);

svg.append("g").attr("transform", "translate(600,550)").call(ch);

// adjust height of frame in bl.ocks.org
d3.select(self.frameElement).style("height", height+"px").style("width", width+"px");
</script>
