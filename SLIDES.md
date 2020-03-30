---
title: A Real-time Geo-social Media Database for Large-scale Coronavirus Disease 2019 (COVID-19) Research
theme: white
---

## A Geo-social Media Database for COVID-19 Research

Richard Wen
<br>rwen@ryerson.ca
<br>March 31, 2020

---

## Second slide

<canvas class="chart stretch">
<!--
{
 "type": "line",
 "data": {
  "labels": ["January"," February"," March"," April"," May"," June"," July"],
  "datasets":[
   {
    "data":[" 65"," 59"," 80"," 81"," 56"," 55"," 40"],
    "label":"My first dataset","backgroundColor":"rgba(20,220,220,.8)"
   },
   {
    "data":[" 28"," 48"," 40"," 19"," 86"," 27"," 90"],
    "label":"My second dataset","backgroundColor":"rgba(220,120,120,.8)"
   }
  ]
 }, 
 "options": { "responsive": "true" }
}
-->
</canvas>

---

## Function plot

<div class="plot" id="myplot1" style="background-color:#fff; width:800px; height:400px; margin: 0 auto;">
<!--
{
 "target":"#myplot1",
 "height":400,
 "width":"800",
 "xAxis":{"domain":[-10,10]},
 "yAxis":{"domain":[-5,5]},
 "grid":true,
 "data":[{"fn":"sin(x)","color":"darkred"}]
}
-->
</div>

---

## Coronavirus (COVID-19)

<canvas width=500 height=500 class="anything">
<!--
{
  "initialize": "function(container) { 
	var width = container.width,
	    height = container.height;
	var projection = d3.geo.orthographic()
	    .translate([width / 2, height / 2])
	    .scale(width / 2 - 20)
	    .clipAngle(90)
	    .precision(0.6);
	var c = container.getContext('2d');
	var path = d3.geo.path()
	    .projection(projection)
	    .context(c);
	d3.queue()
	    .defer(d3.json, 'data/world.json')
	    .defer(d3.tsv, 'data/countries.tsv')
	    .await(ready);
	function ready(error, world, names) {
	  if (error) throw error;
	  var globe = {type: 'Sphere'},
	      land = topojson.feature(world, world.objects.land),
	      countries = topojson.feature(world, world.objects.countries).features,
	      borders = topojson.mesh(world, world.objects.countries, function(a, b) { return a !== b; }),
	      i = -1,
	      n = countries.length;
	  countries = countries.filter(function(d) {
	    return names.some(function(n) {
	      if (d.id == n.id) return d.name = n.name;
	    });
	  }).sort(function(a, b) {
	    return a.name.localeCompare(b.name);
	  });
	  (function transition() {
	    d3.transition()
	        .duration(1250)
	        .each('click', function() {
			while ( !countries[i = (i + 1) % n] ) {};			
	        })
	        .tween('rotate', function() {
	          var p = d3.geo.centroid(countries[i]),
	              r = d3.interpolate(projection.rotate(), [-p[0], -p[1]]);
	          return function(t) {
	            projection.rotate(r(t));
	            c.clearRect(0, 0, width, height);
	            c.fillStyle = '#fff', c.lineWidth = 2, c.beginPath(), path(globe), c.fill();
	            c.fillStyle = '#42affa', c.beginPath(), path(land), c.fill();
	            c.fillStyle = '#f00', c.beginPath(), path(countries[i]), c.fill();
	            c.strokeStyle = '#ccc', c.lineWidth = .5, c.beginPath(), path(borders), c.stroke();
	            c.strokeStyle = '#ccc', c.lineWidth = 2, c.beginPath(), path(globe), c.stroke();
	          };
	        })
	      .transition()
	        .each('end', transition);
	  })();
	}
	d3.select(self.frameElement).style('height', height + 'px');
    }"
}
-->
</canvas>