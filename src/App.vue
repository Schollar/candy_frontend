<template>
  <v-app>
    <v-main>
      <alert-card></alert-card>
      <show-candies></show-candies>
      <change-candy></change-candy>
      <add-candy></add-candy>
      <delete-candy></delete-candy>
    </v-main>
  </v-app>
</template>

<script>
import AddCandy from "./components/AddCandy.vue";
import AlertCard from "./components/AlertCard.vue";
import ChangeCandy from "./components/ChangeCandy.vue";
import DeleteCandy from "./components/DeleteCandy.vue";
import ShowCandies from "./components/ShowCandies.vue";

export default {
  name: "App",

  components: {
    ShowCandies,
    ChangeCandy,
    AddCandy,
    AlertCard,
    DeleteCandy,
  },
};
</script>
