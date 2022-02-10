<template>
  <div>
    <div v-if="show_toast">
      <v-alert dismissible type="success"> {{ api_message }}</v-alert>
    </div>
    <div v-if="show_red_toast">
      <v-alert dismissible type="success" color="red">
        {{ red_message }}</v-alert
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "alert-card",
  data() {
    return {
      api_message: "",
      show_toast: false,
      red_message: "",
      show_red_toast: false,
    };
  },
  // Listening for the global event api message which is sent on every axios request error, and one or two successful requests, and we call the show message function
  mounted() {
    this.$root.$on("api_message", this.show_message);
  },
  methods: {
    // This function takes the string it receives and sets the api message variable to it
    // Then sets the show_toast variable to true to show the notifaction card on the page
    show_message(string) {
      this.api_message = string;
      this.show_toast = true;
    },
    show_red_message(string) {
      this.red_message = string;
      this.show_red_toast = true;
    },
  },
};
</script>
<style scoped>
div {
  position: fixed;
  top: 50%;
  width: 100%;
  z-index: 3;
}
</style>