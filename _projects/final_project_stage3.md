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



<!DOCTYPE HTML>
<html>

<head>
  <meta charset="utf-8">
  <title>interactive_earthquake_map.html</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>

<body>
  <style type="text/css">
    html, body, #container {
      height: 100%;
    }
    body, #container {
      overflow: hidden;
      margin: 0;
    }
    #iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
  <div id="container">
    <iframe id="iframe" sandbox="allow-scripts" src="/asset/visualization_2.html"></iframe>
  </div>
</body>

</html>

