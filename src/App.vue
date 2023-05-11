<template>
  <div class="container">
    <div class="row header">
      <div class="col-xs-11 col-md-12 mx-a">
        <trackerHeader
          :ipAddress="ipAddress"
          :searchResult="searchResult"
          @updateIpAddress="updateIpAddress"
          @searchIp="searchIp"
        >
        </trackerHeader>
      </div>
      <ipMap :ipGeolocalisation="ipGeolocalisation"> </ipMap>
    </div>
  </div>
</template>

<script>
import trackerHeader from "./components/TrackerHeader.vue";
import ipMap from "./components/IpMap.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    trackerHeader,
    ipMap,
  },
  data() {
    return {
      ipAddress: "",
      searchResult: {
        ipAddress: "-",
        ipLocation: "-",
        ipTimezone: "-",
        ipIsp: "-",
      },
      ipGeolocalisation: {
        lat: 0,
        long: 0,
      },
    };
  },
  methods: {
    updateIpAddress(value) {
      this.ipAddress = value;
    },
    searchIp() {
      const ipifyUrl = import.meta.env.VITE_APP_IPIFY_URL;
      const APIKey = import.meta.env.VITE_APP_IPIFY_API_KEY;

      let url = `${ipifyUrl}?apiKey=${APIKey}&ipAddress=${this.ipAddress}`;
      console.log(this.ipAddress);
      fetch(url)
        .then((response) => {
          console.log(url);
          response.json().then((response) => {
            this.searchResult.ipAddress = response.ip;
            this.searchResult.ipLocation = `${response.location.city}, ${response.location.region} ${response.location.postalCode}`;
            this.searchResult.ipTimezone = `UTC ${response.location.timezone}`;
            this.searchResult.ipIsp = response.isp;
            this.ipGeolocalisation.lat = response.location.lat;
            this.ipGeolocalisation.long = response.location.lng;
          });
        })
        .catch((error) => {
          console.log(error);
        })
        .then(() => {
          console.log("done");
        });
    },
  },
};
</script>
