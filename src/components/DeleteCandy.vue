<template>
  <div>
    <h1>Delete Candy!</h1>
    <v-form>
      <v-container>
        <v-text-field
          v-model="candy_title"
          :counter="15"
          label="Candy title to delete"
          required
        ></v-text-field>
        <v-btn @click="delete_candy()">Delete Candy</v-btn>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "delete-candy",
  methods: {
    // Axios request that deletes a candy from the DB
    delete_candy() {
      var candy_title = this.candy_title;
      this.$axios
        .request({
          url: "http://127.0.0.1:5000/candy",
          method: "DELETE",
          data: {
            title: candy_title,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.candy = response.data;
          this.$root.$emit(
            "api_message",
            "You have successfully deleted a candy!"
          );
        })
        .catch((error) => {
          error;
          this.$root.$emit(
            "red_message",
            "Sorry something went deleting the candy. Please try again later"
          );
        });
    },
  },
  data() {
    return {
      candy: [],
      candy_title: "",
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