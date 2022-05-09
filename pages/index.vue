<template>
  <NuxtLayout name='default'>
    <p>Index Page</p>
    <GoogleMaps />
  </NuxtLayout>
</template>

<script lang="ts">
import {defineComponent} from "@vue/runtime-core";
import GoogleMaps from "../components/GoogleMaps";

export default defineComponent({
    components: {
      GoogleMaps
    }
})
</script>

<style scoped>

</style>