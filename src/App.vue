<script>
import { LMap, LTileLayer } from "@vue-leaflet/vue-leaflet";

export default {
  components: {
    LMap,
    LTileLayer
  },
  data() {
    return {
      url_osm: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 15, // riferimento per la visualizzazione, senza questo la mappa non è visibile
      center: [51.505, -0.159], // riferimento per la visualizzazione, senza questo la mappa non è visibile
    };
  }
}
</script>
  

<template>
  <h1>Hello Vue Leaflet</h1>
  <l-map style="height: 300px" :zoom="zoom" :center="center">
    <l-tile-layer :url="url_osm" :attribution="attribution"></l-tile-layer>

  </l-map>
</template>