---
name: Final project stage 3
tools: [Python]

---


We used geopandas to create a geographical plot of the earthquake events. You can see the 
earthquakes on the map, they are color coded by the magnitude and sized by depth. Users can 
use this visualization to gain insights into earthquake occurrences and their spatial distribution 
such as identifying high seismic regions. The patterns can be analyzed to see if there is 
correlation between earthquakes’ magnitude, depth, and geographic locations. Users can 
assess the impacts of recent earthquakes, which can help with disaster preparedness and 
responses


```
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8" />
    <script>L_NO_TOUCH = false; L_DISABLE_3D = false;</script>
    <style>
        html, body {width: 100%; height: 100%; margin: 0; padding: 0;}
        #map {position:absolute; top:0; bottom:0; right:0; left:0;}
    </style>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/leaflet@1.9.3/dist/leaflet.css" />
    <script src="https://cdn.jsdelivr.net/npm/leaflet@1.9.3/dist/leaflet.js"></script>
    <script src="https://code.jquery.com/jquery-1.12.4.min.js"></script>
   
</head>
<body>
    <div id="controls">
        <label for="magType">Magnitude Type:</label>
        <select id="magType" onchange="updateMap()">
            <option value="ml">ml</option>
            <option value="md">md</option>
            
        </select>

        <label for="magnitude">Magnitude:</label>
        <input type="range" id="magnitude" min="1" max="10" onchange="updateMap()">
    </div>

    <div id="map" style="height: 90%;"></div> <

    <script>
        var map = L.map('map', {
            center: [20.0, 0.0],
            zoom: 2,
            zoomControl: true,
            preferCanvas: false
        });

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: 'Data by © OpenStreetMap, under ODbL.',
            maxZoom: 18
        }).addTo(map);

        var markerCluster = L.markerClusterGroup();
        map.addLayer(markerCluster);

        function updateMap() {
            var magType = document.getElementById('magType').value;
            var magnitude = document.getElementById('magnitude').value;
            console.log('Updated Map with:', magType, magnitude);
        
        }
    </script>
</body>
</html>
```
