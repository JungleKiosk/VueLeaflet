
<script>
import { LMap, LTileLayer, LMarker, LTooltip, LPopup } from "@vue-leaflet/vue-leaflet";

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
        LTooltip,
        LPopup
    },
    data() {
        return {
            url_osm: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            attribution:
                '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
            zoom: 15,
            center: [49.410579, 8.715369,],
        };
    },
    methods: {
        getImagePath: function (name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href
        },
        selectMarker: function (marker) {
            this.selectedMarker = marker;
        },
    }

}


</script>
  
  
<template>
    <h1 class="text-center">Hello Vue Leaflet</h1>
    <l-map style="height: 600px" :zoom="zoom" :center="center">
        <l-tile-layer :url="url_osm" :attribution="attribution"></l-tile-layer>

        <template v-for="(coordinate, index) in marker_points" :key="index">
            <l-marker :lat-lng="[coordinate.lat, coordinate.long]" @click="selectMarker(coordinate)">
                <l-tooltip>
                    <div>
                        <!-- <p>id: {{ coordinate.id }}</p> -->
                        <p>City: {{ coordinate.city }}</p>
                        <p>Coordinates: {{ coordinate.lat }} , {{ coordinate.long }}</p>
                    </div>
                </l-tooltip>
                <l-popup>
                    <div>
                        <!-- <p>id: {{ coordinate.id }}</p> -->
                        <p>City: {{ coordinate.city }}</p>
                        <img :src="getImagePath(coordinate.img_popup)" alt="City image: castle or river" />
                        <p>Coordinates: {{ coordinate.lat }} , {{ coordinate.long }}</p>
                    </div>
                </l-popup>
            </l-marker>

        </template>

    </l-map>
</template>