<template>
  <div>
    <h1>{{ msg }}</h1>
    <div id="img-grid">
      <img v-for="(dog, index) in info" :src="dog" width="300" height="300" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      info: null
    };
  },
  mounted() {
    fetch("https://dog.ceo/api/breeds/image/random/9")
      .then(response => response.json())
      .then(response => {
        this.info = response.message;
      });
  }
};
</script>

<style scoped>
#img-grid {
  display: flex;
  flex-wrap: wrap;
  width: 900px;
}
</style>
