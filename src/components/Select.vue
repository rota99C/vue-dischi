<template>
  <div class="container">
    <label for="genres">filtra per genere musicale </label>
    <select>
      <option value="tutti">Tutti</option>
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.container {
  margin-bottom: 70px;
  label {
    color: white;
  }
}
</style>