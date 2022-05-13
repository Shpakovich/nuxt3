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
      /*const geocoder = new MapboxGeocoder({
        accessToken: mapboxgl.accessToken,
        mapboxgl: mapboxgl,
        zoom: 13,
        placeholder: 'Enter an address or place name',
        bbox: [-105.116, 39.679, -104.898, 39.837]
      });*/

      map.addControl(geoLocate);
      map.on('load', () => {
        geoLocate.trigger();
        // map.addControl(geocoder, 'top-left');
      });

      addPopUp();
      function addPopUp() {
        const popup = featurePopup();
        const el = document.createElement('div');
        el.id = 'marker';

        return new mapboxgl.Marker()
            .setLngLat([131.9034467, 43.1027089])
            .setPopup(popup)
            .addTo(map);
      }
      function featurePopup() {
        return new mapboxgl.Popup({offset: 25}).setText(
            'Construction on the Washington Monument began in 1848.'
        )
      }

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