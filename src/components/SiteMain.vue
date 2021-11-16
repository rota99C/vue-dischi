<template>
  <div id="main">
    <Select @filterElement="filterGenre" />
    <div class="container-product">
      <Product
        v-for="song in songs"
        :key="song.genre"
        :image="song.poster"
        :title="song.title"
        :author="song.author"
        :year="song.year"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Product from "./Product.vue";
import Select from "./Select.vue";

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
  methods: {
    filterGenre(value) {
      this.selection = value;
      console.log(value);
    },
  },
  components: { Product, Select },
};
</script>

<style lang="scss">
#main {
  background-color: #1e2d3b;
  width: 100%;
  padding: 40px 20px;
  text-align: center;
}
.container-product {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>