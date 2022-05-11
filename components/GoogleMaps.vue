<template>
  <div id='map'></div>
</template>

<script lang="ts">
import {defineComponent, onMounted} from "@vue/runtime-core";
import mapboxgl from "mapbox-gl";

mapboxgl.accessToken = 'pk.eyJ1IjoiZGVuaXMyNTAzIiwiYSI6ImNsMnlzNWp2YTB4cnQzbGs0ZjQ4dXg2MGIifQ.kSlUTa5dNY4DSNLDTKsdyA';

export default defineComponent({
  setup() {
    onMounted(async ()=>{
      const map = await new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/mapbox/streets-v11',
        // center: [131.9034467, 43.1027089],
        center: [37.587874, 55.73367],
        zoom: 2,
        attributionControl: true
      });

      // Add geolocate control to the map.
      const geoLocate = new mapboxgl.GeolocateControl({
            positionOptions: {
              enableHighAccuracy: true
            },
            trackUserLocation: false
          });
      map.addControl(geoLocate);
      map.on('load', () => {
        geoLocate.trigger();
      });

      const marker1 = new mapboxgl.Marker()
          .setLngLat([37.587874, 55.73367])
          .addTo(map);

      /*const geocoder = new MapboxGeocoder({
        // Initialize the geocoder
        accessToken: mapboxgl.accessToken, // Set the access token
        mapboxgl: mapboxgl, // Set the mapbox-gl instance
        zoom: 13, // Set the zoom level for geocoding results
        placeholder: 'Enter an address or place name', // This placeholder text will display in the search bar
        bbox: [-105.116, 39.679, -104.898, 39.837] // Set a bounding box
      });
      map.addControl(geocoder, 'top-left');*/
    })

  },
})
</script>

<style scoped>
  #map {
    display: flex;
    top: 0;
    bottom: 0;
    width: 500px;
    height: 500px;
    border-radius: 8px;
  }
</style>