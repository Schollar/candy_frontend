<template>
  <v-app>
    <v-main>
      <show-candies></show-candies>
      <change-candy></change-candy>
    </v-main>
  </v-app>
</template>

<script>
import ChangeCandy from "./components/ChangeCandy.vue";
import ShowCandies from "./components/ShowCandies.vue";

export default {
  name: "App",

  components: {
    ShowCandies,
    ChangeCandy,
  },
};
</script>
