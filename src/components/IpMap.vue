<template>
  <div class="col-xs-12 col-md-12 map-wrapper">
    <div id="map"></div>
  </div>
</template>

<script>
import L from "leaflet";

import iconImg from "../assets/images/icon-location.svg";

export default {
  name: "ipMap",
  data() {
    return {
      map: [],
    };
  },
  props: {
    ipGeolocalisation: {
      lat: Number,
      long: Number,
    },
  },
  watch: {
    ipGeolocalisation: {
      handler(val) {
        this.map.setView([val.lat, val.long]);
        const ipIcon = L.icon({
          iconUrl: iconImg,
          iconSize: [46, 56],
          iconAnchor: [23, 56],
        });
        console.log(ipIcon);
        L.marker([val.lat, val.long], { icon: ipIcon }).addTo(this.map);
      },
      deep: true,
    },
  },
  mounted() {
    const map = L.map("map", {
      zoomControl: false,
    }).setView([51.505, -0.09], 13);
    L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
      maxZoom: 19,
      attribution:
        '&copy; OpenStreetMap France | &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(map);
    this.map = map;
  },
};
</script>
