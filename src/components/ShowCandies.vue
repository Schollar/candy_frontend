<template>
  <div>
    <h1>Posts</h1>
    <v-btn @click="get_candies()">GET CANDY POSTS</v-btn>
    <div v-for="candy in candies" :key="candy[0]">
      <p>{{ candy[0] }}: {{ candy[1] }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "show-candies",
  methods: {
    get_candies() {
      this.$axios
        .request({
          url: "http://127.0.0.1:5000/candy",
        })
        .then((response) => {
          this.candies = response.data;
        })
        .catch((error) => {
          error;
          this.$root.$emit(
            "api_message",
            "Sorry something went wrong with logging in. Please try again later"
          );
        });
    },
  },
  data() {
    return {
      candies: [],
    };
  },
};
</script>

<style scoped>
div {
  display: grid;
  place-items: center;
}
</style>