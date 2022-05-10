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
      await new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/mapbox/light-v10',
        center: [-96, 37.8],
        zoom: 3
      });
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
  }
</style>