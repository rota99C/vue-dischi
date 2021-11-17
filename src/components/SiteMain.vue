<template>
  <div id="main">
    <Select :genres="getGenres" @filterElement="filterGenre" />
    <div class="container-product">
      <Product
        v-for="song in filterDisks"
        :song="song"
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
      genre: "",
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.songs = response.data.response;
        // console.log(this.songs);
      })
      .catch((error) => {
        console.error(error);
      });
  },
  methods: {
    setGenre(genre) {
      //console.log(genre);
      this.genre = genre;
    },
    filterGenre(value) {
      this.selection = value;
      console.log(value);
      const filteredElements = this.songs.filter((song) => {
        return song.genre.includes(value);
      });
      console.log(filteredElements);
    },
  },
  computed: {
    getGenres() {
      let genres = [];
      this.songs.forEach((song) => {
        //console.log(disk.genre, genres.includes(disk.genre));
        if (!genres.includes(song.genre)) {
          genres.push(song.genre);
        }
        //console.log(genres);
      });
      //console.log(genres);
      return genres;
    },
    filteredDisks() {
      if (this.genre === "") {
        return this.songs;
      } else if (this.genre !== "") {
        return this.songs.filter((song) => song.genre === this.genre);
      }
      console.log("Fuori da tutto");
      return this.disks.filter(
        (disk) => disk.genre === this.genre || disk.author === this.artist
      );
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