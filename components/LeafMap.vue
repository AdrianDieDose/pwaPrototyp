<template>
  <div class="map">
    <l-map
      ref="map"
      style="height: 500px"
      :zoom="zoom"
      :center="center"
      @update:center="centerUpdated"
    >
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <!-- <l-marker :lat-lng="markerLatLng"></l-marker>
      <l-marker :lat-lng="markerLatLng1"></l-marker>
      <l-marker :lat-lng="markerLatLng2"></l-marker>
      <l-marker
        v-for="item in testCords"
        :key="item.cord1"
        :lat-lng="[item.cord1, item.cord2]"
      ></l-marker>
    
    
    <p v-for="item in testCords" :key="item.cord1">{{ item.cord2 }}</p> -->
    </l-map>
  </div>
</template>

<script>
import {
  LMap,
  LTileLayer,
  LMarker,

  //LCircleMarker
} from 'vue2-leaflet'

export default {
  props: {
    testCords: Array,
  },
  components: {
    LMap,
    LTileLayer,
    LMarker,
    //LCircleMarker,
  },
  data() {
    return {
      map: null,
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 15,
      center: [52.0265, 8.5308],
      markerLatLng: [52.0265, 8.5308],
      markerLatLng1: [52.0304, 8.5302],
      markerLatLng2: [52.0235, 8.5308],
      circleCenter: [52.0265, 8.5308],
      circle: {
        center: [52.0265, 8.5308],
        radius: 150,
        color: 'red',
      },
    }
  },
  methods: {
    centerUpdated(center) {
      this.circle.center = center
    },
  },
  test() {
    console.log('gg')
  },
}
</script>
<style scoped>
.map {
  margin: 0% 5%;
}
</style>
