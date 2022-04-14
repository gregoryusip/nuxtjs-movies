<template>
  <div>
    <!-- <navigation></navigation> -->
    <nuxt />
  </div>
</template>

<script>
import Navigation from "@/components/Navigation.vue";
import axios from "axios";

axios.defaults.headers.common["user-key"] = "2e0ec924191ee1585a8ddadf6b7f1d7a";

export default {
  components: {
    Navigation,
  },
};
</script>
