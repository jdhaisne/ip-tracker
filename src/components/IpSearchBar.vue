<template>
  <div class="row search-bar-wrapper">
    <div class="row col-xs-12 search-bar">
      <div class="col-10">
        <input
          :value="ipAddress"
          @input="$emit('updateInput', $event.target.value)"
          class="search-bar search-bar__input"
          type="text"
          placeholder="192.212.174.101"
        />
      </div>
      <button
        @click="$emit('searchIp')"
        class="col-2 search-bar search-bar__button"
      >
        <img
          class="search-bar__arrow"
          src="/assets/images/icon-arrow.svg"
          alt="arrow"
        />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ipSearchBar",
  props: {
    ipAddress: String,
  },
};
</script>
