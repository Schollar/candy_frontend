<template>
  <div>
    <h1>Change Candy!</h1>
    <v-form>
      <v-container>
        <v-text-field
          v-model="candy_title"
          :counter="15"
          label="Candy Title"
          required
        ></v-text-field>
        <v-text-field
          v-model="candy_new_title"
          :counter="15"
          label="Candy new title"
          required
        ></v-text-field>
        <v-text-field
          v-model="candy_content"
          :counter="50"
          label=" New Content"
        ></v-text-field>
        <v-btn @click="change_candy()">Change Candy Post</v-btn>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "change-candy",
  methods: {
    // Axios request that gets user input to change the title and content of a candy
    change_candy() {
      var candy_title = this.candy_title;
      var candy_content = this.candy_content;
      var candy_new_title = this.candy_new_title;
      this.$axios
        .request({
          url: "http://127.0.0.1:5000/candy",
          method: "PATCH",
          data: {
            title: candy_title,
            content: candy_content,
            new_title: candy_new_title,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.candy = response.data;
          this.$root.$emit(
            "api_message",
            "You have successfully changed a candy!"
          );
        })
        .catch((error) => {
          error;
          this.$root.$emit(
            "red_message",
            "Sorry something went wrong with changing candy. Please try again later"
          );
        });
    },
  },
  data() {
    return {
      candy: [],
      candy_title: "",
      candy_new_title: "",
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