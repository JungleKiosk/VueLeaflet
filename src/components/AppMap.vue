
<script>
import { LMap, LTileLayer, LMarker, LTooltip } from "@vue-leaflet/vue-leaflet";

export default {
    props: {
        marker_points: {
            type: Array,
            required: true
        }
    },
    components: {
        LMap,
        LTileLayer,
        LMarker,
        LTooltip
    },
    data() {
        return {
            url_osm: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            attribution:
                '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
            zoom: 15,
            center: [49.410579, 8.715369,],
        };
    }
}


</script>
  
  
<template>
    <h1 class="text-center">Hello Vue Leaflet</h1>
    <l-map style="height: 300px" :zoom="zoom" :center="center">
        <l-tile-layer :url="url_osm" :attribution="attribution"></l-tile-layer>

        <template v-for="(coordinate, index) in marker_points" :key="index">
            <l-marker :lat-lng="[coordinate.lat, coordinate.long]">
                <l-tooltip>
                    <div>
                        <!-- <p>id: {{ coordinate.id }}</p> -->
                        <p>City: {{ coordinate.city }}</p>
                        <p>Coordinates: {{ coordinate.lat }} , {{ coordinate.long }}</p>
                    </div>
                </l-tooltip>
            </l-marker>

        </template>

    </l-map>
</template>