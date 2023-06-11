<script>
import { marker_points } from "./data/markers.js";
import AppMap from "./components/AppMap.vue";

export default {
  components: {
    AppMap
  },
  data() {
    return {
      marker_points: marker_points
    };
  }
}
</script>


<template>
  <div>
    <AppMap :marker_points="marker_points"></AppMap>
  </div>
</template>

