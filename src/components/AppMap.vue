
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
            center: [49.411905, 8.728353],
            selectedMarker: null
        };
    },
    methods: {
        getImagePath: function (name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href
        },
        selectMarker: function (marker) {
            this.selectedMarker = marker;
        },
        selectImage(image) {
            this.selectedMarker.img_popup = image.img_card;
        },
        closeMarkerCard() {
            this.selectedMarker = null;
        },
    },
    computed: {
        mapColumnClass() {
            return this.selectedMarker ? 'col-12 col-lg-6' : 'col-12 col-lg-12';
        },
    }
}


</script>
  
  
<template>
    <div class="container">
        <h1 class="text-center">Hello Vue Leaflet</h1>
        <div class="row">
            <div :class="mapColumnClass">
                <l-map style="height: 600px" :zoom="zoom" :center="center">
                    <l-tile-layer :url="url_osm" :attribution="attribution"></l-tile-layer>

                    <template v-for="(coordinate, index) in marker_points" :key="index">
                        <l-marker :lat-lng="[coordinate.lat, coordinate.long]" @click="selectMarker(coordinate)">
                            <l-tooltip>
                                <div>
                                    <!-- <p>id: {{ coordinate.id }}</p> -->
                                    <p>{{ coordinate.city }}</p>
                                    <p>{{ coordinate.lat }} , {{ coordinate.long }}</p>
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
            </div>
            <!-- /.col-6 col-lg-6 -->
            <div class="col-12 col-lg-4">
                <div v-if="selectedMarker">
                    <div class="marker_card">
                        <div class="row justify-content-end">
                            <div class="col-2">
                                <button class=" btn-close close_button " @click="closeMarkerCard"></button>
                            </div>
                        </div>
                        <div class="row">
                            <p>Images</p>
                            <div class="col-3 col-lg-3" v-for="(image, index) in selectedMarker.img_marker_card" :key="index"
                                @click="selectImage(image)">
                                <img :src="getImagePath(image.img_card)" :alt="image.img_card" class="img-fluid rounded-3" />
                            </div>
                            <div class="col-12 col-lg-12">
                                <img :src="getImagePath(selectedMarker.img_popup)" alt="Marker Image" class=" rounded-5" />
                            </div>
                           
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- /.row -->
    </div>
    <!-- /.container -->
</template>