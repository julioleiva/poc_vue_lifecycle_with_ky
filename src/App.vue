<template>
  <div id="app">
    <h2>POC KY.js y Ciclos de vida</h2>
    <div>
      <a href="https://es.vuejs.org/v2/guide/instance.html">Instancia VUE</a>
    </div>
  </div>
</template>

<script>
import ky from "ky";

async function fetchData() {
  let response = await ky("https://jsonplaceholder.typicode.com/posts");
  let body = await response.json();
  return body;
}

export default {
  name: "App",
  beforeCreate() {
    // Se inician los eventos y el ciclo de vida
    console.log("beforeCreate, sin acceso a la data. Data:", this.posts);
  },
  created() {
    // Se inician las injections y la reactividad
    console.log("created, con acceso a la data. Data:", this.posts);
    fetchData();
  },
  beforeMount() {},
  mounted() {
    console.log(this.$data);
  },
  beforeUpdate() {},
  update() {},
  beforeDestroy() {},
  destroyed() {},

  data() {
    return {
      posts: [],
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
