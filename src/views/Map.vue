<template>
  <div id="map">
    <div id="circle"></div>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";

export default {
  name: "LeafletMap",
  data() {
    return {
      map: null
    };
  },
  mounted() {
    this.map = L.map("map").setView([-36.8232844,-73.0448676], 24);
    L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(this.map);
    var closedIcon = L.icon({
      iconUrl: 'https://i.imgur.com/vfhgCUG.png',
      iconSize: [32, 32]
    });
    var guanacoIcon = L.icon({
      iconUrl: 'https://i.imgur.com/0ydOdUp.png',
      iconSize: [32, 32]
    });
    L.marker([-36.8229,-73.0448], {icon: closedIcon}).addTo(this.map);
    L.marker([-36.8216,-73.0448], {icon: guanacoIcon}).addTo(this.map);
  },
  beforeDestroy() {
    if (this.map) {
      this.map.remove();
    }
  }
};
</script>

<style scoped>
#map {
  width: 100vw;
  height: 100vh;
}
</style>