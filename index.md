<html>
  <head>
        <title>City of Austin - Libraries</title>
        <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.css" />
        <script src="http://cdn.leafletjs.com/leaflet-0.7.2/leaflet.js"></script>
        <script src="http://code.jquery.com/jquery-1.10.2.min.js"></script>
        <style>
        body {padding: 0; margin: 0 }
        html, body, #map { height: 100% }
        </style>
  </head>

  <body>
        <div id="map"></div>
        <script type ="text/javascript">
        var basemap = L.tileLayer(
                'http://{s}.tiles.mapbox.com/v3/sarasafavi.hjegnofh/{z}/{x}/{y}.png',
                                  {     maxZoom: 18     });

        $.getJSON('libraries.json', function(data) {
                var geojson = L.geoJson(data, {
                  onEachFeature: function (feature, layer) {
                          layer.bindPopup(feature.properties.NAME + '<br />'
                                                        + feature.properties.ADDRESS);
                  }
                });
        var map = L.map('map').setView([30.260, -97.770], 12);
        basemap.addTo(map);
        geojson.addTo(map);
        });

  </script>
 </body>
</html>
