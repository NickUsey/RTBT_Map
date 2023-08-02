# RTBT_Map

<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>Map Animation</title>
    <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no" />
    <script src="https://api.mapbox.com/mapbox-gl-js/v1.11.0/mapbox-gl.js"></script>
    <link href="https://api.mapbox.com/mapbox-gl-js/v1.11.0/mapbox-gl.css" rel="stylesheet" />
    <link href="./styles.css" rel="stylesheet" />
</head>
<body>
    <div id="map"></div>
    <div class="map-overlay top">
        <button style="font-size: 2em" onclick="move()">
            Show stops between MIT and Harvard
        </button>
    </div>
 <script>
    const busStops = [
      [-71.093729, 42.359244],
      [-71.094915, 42.360175],
      [-71.0958, 42.360698],
      [-71.099558, 42.362953],
      [-71.103476, 42.365248],
      [-71.106067, 42.366806],
      [-71.108717, 42.368355],
      [-71.110799, 42.369192],
      [-71.113095, 42.370218],
      [-71.115476, 42.372085],
      [-71.117585, 42.373016],
      [-71.118625, 42.374863],
    ];
    mapboxgl.accessToken = 'pk.eyJ1IjoidGVzdHVzZXIxMDAwIiwiYSI6ImNraDkzZ2pkMzAzMHoycnBmMXpvZ3UwZnMifQ.jAE4YsPeAJv50VK92NSpOQ';
let map = new mapboxgl.Map({
  container: 'map',
  style: 'mapbox://styles/mapbox/streets-v11',
  center: [-71.104081, 42.365554],
  zoom: 14,
});
let marker = new mapboxgl.Marker().setLngLat([-71.092761, 42.357575]).addTo(map);
let counter = 0;
function move() {
setTimeout(() => {
    if (counter >= busStops.length) return;
    marker.setLngLat(busStops[counter]);
    counter++;
    move();
  }, 1000);
}
if (typeof module !== 'undefined') {
  module.exports = { move, counter, marker, busStops };
}
</script>
    
<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
.map-overlay {
  position: absolute;
  left: 0;
  padding: 10px;
}
</style>
</body>
</html>
