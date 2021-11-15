<template>
  <div class="singolo">
    <img :src="image" alt="" />
    <h5>{{ title }}</h5>
    <p>{{ author }}</p>
    <p>{{ year }}</p>
  </div>
</template>
<script>
export default {
  props: {
    image: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style lang="scss">
.singolo {
  width: 200px;
  height: 360px;
  background-color: #2e3a46;
}
img {
  width: 160px;
  height: 160px;
}
h5 {
  color: white;
  font-weight: lighter;
}
</style>