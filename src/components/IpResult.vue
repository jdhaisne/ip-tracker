<template>
  <div class="row search-result-wrapper">
    <div class="row col-xs-12 search-result">
      <div class="col-10 search-result__text-wrapper row">
        <p class="search-result__title col-12">ip address</p>
        <p class="search-result__text col-12">{{ searchResult.ipAddress }}</p>
      </div>
      <div class="col-10 search-result__text-wrapper row">
        <p class="search-result__title col-12">location</p>
        <p class="search-result__text col-12">{{ searchResult.ipLocation }}</p>
      </div>
      <div class="col-10 search-result__text-wrapper row">
        <p class="search-result__title col-12">timezone</p>
        <p class="search-result__text col-12">{{ searchResult.ipTimezone }}</p>
      </div>
      <div class="col-10 search-result__text-wrapper row">
        <p class="search-result__title col-12">isp</p>
        <p class="search-result__text col-12">{{ searchResult.ipIsp }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ipResult",
  props: {
    searchResult: {
      ipAddress: String,
      ipLocation: String,
      ipTimezone: String,
      ipIsp: String,
    },
  },
};
</script>
