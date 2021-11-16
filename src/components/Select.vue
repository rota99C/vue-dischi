<template>
  <div class="container">
    <label for="genres">filtra per genere musicale </label>
    <select v-model="selection" @change="changeSelection">
      <option value="tutti">Tutti</option>
      <option v-for="(genre, i) in genres" :key="i" :value="genre">
        {{ genre }}
      </option>

      <!-- option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="jazz">Jazz</option>
      <option value="Metal">Metal</option> -->
    </select>
  </div>
</template>

<script>
import axios from "axios";
export default {
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        response.data.response.forEach((element) => {
          if (!this.genres.includes(element.genre)) {
            this.genres.push(element.genre);
          }
        });
        console.log(this.songs.genres);
      })
      .catch((error) => {
        console.error(error);
      });
  },
  data() {
    return {
      selection: "",
      genres: [],
    };
  },
  methods: {
    changeSelection() {
      this.$emit("filterElement", this.selection);
      console.log(this.selection);
    },
  },
};
</script>

<style lang="scss">
.container {
  margin-bottom: 70px;
  label {
    color: white;
  }
}
</style>