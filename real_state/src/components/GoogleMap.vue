<template>
  <div id="map" class="map-container">
    <iframe aria-hidden="true" frameborder="0" tabindex="-1" style="z-index: -1; position: absolute; width: 100%; height: 100%; top: 0px; left: 0px; border: none; opacity: 0;"></iframe>
  </div>
</template>

<script>
import L from 'leaflet';
import 'leaflet/dist/leaflet.css';

export default {
  name: 'LeafletMap',
  mounted() {
    const map = L.map('map').setView([51.505, -0.09], 13);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    }).addTo(map);

    L.marker([51.505, -0.09]).addTo(map)
      .bindPopup('my location')
      .openPopup();
  },
};
</script>

<style scoped>
.map-container {
  width: 100%;
  height: 300px;
  border-radius: 13px;
  position: relative;
}
</style>
