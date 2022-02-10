<template>
  <div>
    <h1>Post a new Candy!</h1>
    <v-form>
      <v-container>
        <v-text-field
          v-model="candy_title"
          :counter="15"
          label="Candy Title"
          required
        ></v-text-field>

        <v-text-field
          v-model="candy_content"
          :counter="50"
          label="Description"
          required
        ></v-text-field>
        <v-btn @click="add_candy()">Post Candy</v-btn>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "add-candy",
  methods: {
    // Axios request that gets user input to insert a new candy post to the DB
    add_candy() {
      var candy_title = this.candy_title;
      var candy_content = this.candy_content;
      this.$axios
        .request({
          url: "http://127.0.0.1:5000/candy",
          method: "POST",
          data: {
            title: candy_title,
            content: candy_content,
          },
        })
        .then((response) => {
          this.candy = response.data;
          this.$root.$emit(
            "api_message",
            "You have successfully posted a new candy!"
          );
        })
        .catch((error) => {
          error;
          this.$root.$emit(
            "red_message",
            "Sorry something went wrong with posting. Please try again later"
          );
        });
    },
  },
  data() {
    return {
      candy: [],
      candy_title: "",
      candy_content: "",
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