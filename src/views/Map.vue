<template>
  <div>
    <div id="map">
    </div>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";

export default {
  name: "LeafletMap",
  data() {
    return {
      lat: 1,
      lng: 2,
      map: null
    };
  },
  mounted() {
    alert(this.lat+', '+this.lng);
    navigator.geolocation.getCurrentPosition(
      function(pos) {
        var crd = pos.coords;
        console.log('Your current position is:');
        console.log('Latitude : ' + crd.latitude);
        console.log('Longitude: ' + crd.longitude);
        console.log('More or less ' + crd.accuracy + ' meters.');
      },
      function(err) {
        console.warn('ERROR(' + err.code + '): ' + err.message);
      },
      {
        enableHighAccuracy: true,
        timeout: 5000,
        maximumAge: 0
      }
    );
    alert(this.lat+', '+this.lng);
    if (!this.gettingLocation) {
      this.map = L.map("map", {doubleClickZoom: false}).locate({setView: true, maxZoom: 16});
    } else {
      this.map = L.map("map", {doubleClickZoom: false})
    }
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
  height: 80vh;
}
</style>