<template>
  <div id="map" style="height: 100vh;"></div>
  <q-page padding>
    <!-- sadržaj -->
  </q-page>
</template>

<script>
import { ref, onMounted } from 'vue';
import * as L from 'leaflet';
import "leaflet/dist/leaflet.css";

export default {
  setup(){
    const initialMap = ref(null);
    
    onMounted(() => {
        initialMap.value = L.map('map').setView([45.3312, 14.4322], 13);

        L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 19,
            attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
        }).addTo(initialMap.value);
        
        // Dodavanje markera na specifičnu lokaciju
        const marker = L.marker([45.3312, 14.4322]).addTo(initialMap.value);
        marker.bindPopup("Ovdje je knjižnica!").openPopup();
      });
      
    return {
      initialMap
    }
  }
}
</script>
