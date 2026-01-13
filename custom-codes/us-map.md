```html
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
/>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<!-- Leaflet JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // Initialize map (USA centered)
  var map = L.map('map').setView([39.5, -98.35], 4);

  // OpenStreetMap tiles
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 18,
    attribution: '© OpenStreetMap'
  }).addTo(map);

  // ===== Locations (Example service points) =====
  var locations = [
    { name: "Montana", coords: [46.8797, -110.3626] },
    { name: "Wyoming", coords: [43.0759, -107.2903] },
    { name: "Idaho", coords: [44.0682, -114.7420] },
    { name: "North Dakota", coords: [47.5515, -100.7837] },
    { name: "South Dakota", coords: [43.9695, -99.9018] },
    { name: "Nebraska", coords: [41.4925, -99.9018] }
  ];

  // Marker group
  var markers = L.layerGroup();

  locations.forEach(function (loc) {
    L.marker(loc.coords)
      .bindPopup("<strong>" + loc.name + "</strong><br>Service Area")
      .addTo(markers);
  });

  markers.addTo(map);

});
</script>
```
