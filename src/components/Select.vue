<template>
  <div class="container">
    <label for="genres">filtra per genere musicale </label>
    <select v-model="selection" @change="changeSelection">
      <option v-for="(genre, i) in genres" :key="i" :value="genre">
        {{ genre }}
      </option>
      <!-- <option value="tutti">Tutti</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="jazz">Jazz</option>
      <option value="Metal">Metal</option> -->
    </select>
  </div>
</template>

<script>
export default {
  props: {
    genres: [],
  },
  data() {
    return {
      selection: "",
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