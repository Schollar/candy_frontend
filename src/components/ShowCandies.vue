<template>
  <div>
    <h1>Posts</h1>
    <!-- A button that calls the function. And we loop over the candies list to show each post on the page -->
    <v-btn @click="get_candies()">GET CANDY POSTS</v-btn>
    <div v-for="candy in candies" :key="candy[3]">
      <p>{{ candy[0] }}: {{ candy[1] }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "show-candies",
  methods: {
    // Axios request that gets all the candy posts from the DB and stores them to a list
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
            "red_message",
            "Sorry something went wrong with getting candies. Please try again later"
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