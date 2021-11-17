<template>
  <div class="singolo">
    <img :src="image" alt="" />
    <h2>{{ title }}</h2>
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
    song: Object,
  },
};
</script>

<style lang="scss">
.singolo {
  width: 200px;
  height: 360px;
  background-color: #2e3a46;
  text-align: center;
  margin: 20px 20px;
  padding: 15px;
}
img {
  width: 160px;
  height: 160px;
  margin-bottom: 25px;
}
h2 {
  color: white;
  font-weight: lighter;
  margin-bottom: 15px;
}

p {
  color: #808080;
}
</style>