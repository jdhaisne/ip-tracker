<template>
  <header>
    <div class="title-wrapper">
      <h1 class="title">IP Address Tracker</h1>
    </div>
    <ipSearchBar
      :ipAddress="ipAddress"
      @searchIp="$emit('searchIp')"
      @updateInput="updateInput"
    >
    </ipSearchBar>
    <ipResult :searchResult="searchResult"> </ipResult>
  </header>
</template>

<script>
import ipSearchBar from "./IpSearchBar.vue";
import ipResult from "./IpResult.vue";

export default {
  name: "trackerHeader",
  components: {
    ipSearchBar,
    ipResult,
  },
  props: {
    ipAddress: String,
    searchResult: {
      ipAddress: String,
      ipLocation: String,
      ipTimezone: String,
      ipIsp: String,
    },
  },
  methods: {
    searchIp() {
      // eslint-disable-next-line
      alert(this.ipAddress);
    },
    updateInput(value) {
      this.$emit("updateIpAddress", value);
    },
  },
};
</script>
