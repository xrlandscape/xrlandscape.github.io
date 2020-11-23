---
layout: map
title: XR Map
---

<h1 style="text-align:center;"> XR Map</h1>
<h4 style="text-align:center;">(in development)</h4>

<main style=" height: 100vh">
	<div id="map" style="width: 100%; height:100%;"></div>
</main>

<script>
    
	var mymap = L.map('map').setView([27, 0], 3.5);

	L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw', {
		minZoom: 3.5,
		maxZoom: 18,
		attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, ' +
			'<a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
			'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
		id: 'mapbox/streets-v11',
		tileSize: 512,
		zoomOffset: -1,
		  maxBoundsViscosity: 1.0,
		noWrap: true  
	}).addTo(mymap);


    {% for item in site.data.studios %}
        L.marker([ {{ item.location }}]).addTo(mymap)
		.bindPopup("<b>{{ item.name }}</b><br/>{{ item.info}}<br/><a href='{{ item.url }}' target='_blank'>{{ item.url| truncate: 30  }}</a>");
    {% endfor %}

</script>



