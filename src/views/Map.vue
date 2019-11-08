<template>
  <div>
    <b-row>
      <b-col>
      <div id="map"></div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";

export default {
  name: "LeafletMap",
  data() {
    return {
      rtl: true,
      rtltext: 'Desactivar',
      map: null
    };
  },
  mounted() {
    var map = L.map("map", {doubleClickZoom: false})
    var layerGroup = L.layerGroup().addTo(map);
    var userIcon = L.icon({
      iconUrl: 'https://i.imgur.com/3AnBYbC.png',
      iconSize: [32, 32]
    });
    L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    var closedIcon = L.icon({
      iconUrl: 'https://i.imgur.com/vfhgCUG.png',
      iconSize: [32, 32]
    });
    var guanacoIcon = L.icon({
      iconUrl: 'https://i.imgur.com/0ydOdUp.png',
      iconSize: [32, 32]
    });
    var pacosIcon = L.icon({
      iconUrl: 'https://i.imgur.com/g5Cenpx.png',
      iconSize: [32, 32]
    });
    var helpIcon = L.icon({
      iconUrl: 'https://i.imgur.com/0XObLbV.png',
      iconSize: [32, 32]
    });
    var patrullaIcon = L.icon({
      iconUrl: 'https://i.imgur.com/igrHsR1.png',
      iconSize: [32, 32]
    });

    function onLocationFound(e) {
      layerGroup.clearLayers();
      var radius = e.accuracy / 4;
      L.marker(e.latlng, {icon: userIcon}).addTo(layerGroup)
      L.circle(e.latlng, radius).addTo(layerGroup);
    }
    if (this.rtl) {
      map.on('locationfound', onLocationFound);
      map.locate({setView: true, watch: true, maxZoom: 16});
    }

    L.marker([-36.8272,-73.0398], {icon: closedIcon}).addTo(map);
    L.marker([-36.8247,-73.0398], {icon: guanacoIcon}).addTo(map);
    L.marker([-36.8272,-73.0458], {icon: pacosIcon}).addTo(map);
    L.marker([-36.8292,-73.0378], {icon: helpIcon}).addTo(map);
    L.marker([-36.8250,-73.0382], {icon: helpIcon}).addTo(map);
    L.marker([-36.8262,-73.0378], {icon: patrullaIcon}).addTo(map);
    this.map = map
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