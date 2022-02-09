<template>
  <v-app>
    <v-main>
      <show-candies></show-candies>
      <change-candy></change-candy>
      <add-candy></add-candy>
    </v-main>
  </v-app>
</template>

<script>
import AddCandy from "./components/AddCandy.vue";
import ChangeCandy from "./components/ChangeCandy.vue";
import ShowCandies from "./components/ShowCandies.vue";

export default {
  name: "App",

  components: {
    ShowCandies,
    ChangeCandy,
    AddCandy,
  },
};
</script>
