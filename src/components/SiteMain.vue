<template>
  <div id="main">
    <Product
      v-for="song in songs"
      :key="song.genre"
      :image="song.poster"
      :title="song.title"
      :author="song.author"
      :year="song.year"
    />
  </div>
</template>

<script>
import axios from "axios";
import Product from "./Product.vue";

export default {
  data() {
    return {
      songs: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.songs = response.data.response;
        console.log(this.songs);
      })
      .catch((error) => {
        console.error(error);
      });
  },
  components: { Product },
};
</script>

<style lang="scss">
#main {
  background-color: #1e2d3b;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  padding: 100px 20px;
  justify-content: center;
}
</style>