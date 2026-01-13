<img width="3328" height="1912" alt="image" src="https://github.com/user-attachments/assets/c3e5f4c7-22b5-43c2-83b0-c1428fbd7f98" />

```html
<!-- MAP STYLES -->
<style>
  #usMap {
    width: 100%;
    height: 600px;      /* clean default height */
    margin: 80px 0;     /* spacing so sections don’t overlap */
  }
</style>

<!-- MAP CONTAINER -->
<div id="usMap"></div>

<!-- LEAFLET CSS -->
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
/>

<!-- LEAFLET JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<!-- MAP SCRIPT -->
<script>
document.addEventListener("DOMContentLoaded", function () {

  // Manually tuned center & zoom for perfect framing
  var map = L.map('usMap', {
    scrollWheelZoom: true
  }).setView([44.0, -104.5], 5);

  // OpenStreetMap tiles (natural labels)
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 18,
    attribution: '© OpenStreetMap'
  }).addTo(map);

  // Service locations
  var locations = [
    { name: "Montana", coords: [46.8797, -110.3626] },
    { name: "Idaho", coords: [44.0682, -114.7420] },
    { name: "Wyoming", coords: [43.0759, -107.2903] },
    { name: "North Dakota", coords: [47.5515, -100.7837] },
    { name: "South Dakota", coords: [43.9695, -99.9018] },
    { name: "Nebraska", coords: [41.4925, -99.9018] }
  ];

  // Add markers
  locations.forEach(function (loc) {
    L.marker(loc.coords)
      .bindPopup("<strong>" + loc.name + "</strong><br>Service Area")
      .addTo(map);
  });

});
</script>
```
