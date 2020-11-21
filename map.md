---
layout: default
title: Map
---



<div id="map" style="width: 100%; height: 500px;"></div>
<script>
    
	var mymap = L.map('map').setView([20, 0], 2);

	L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw', {
		maxZoom: 16,
		attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, ' +
			'<a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
			'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
		id: 'mapbox/streets-v11',
		tileSize: 512,
		zoomOffset: -1  
	}).addTo(mymap);


    {% for item in site.data.studios %}
        L.marker([ {{ item.location }}]).addTo(mymap)
		.bindPopup("<b>{{ item.name }}</b><br/>{{ item.info}}<br/><a href='{{ item.url }}' target='_blank'>{{ item.url| truncate: 30  }}</a>");
    {% endfor %}

</script>



