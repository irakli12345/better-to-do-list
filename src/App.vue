<template>
  <div id="app">
    <HelloWorld msg="Things you have to do" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 0;
}
body {
  margin: 0 !important;
  background-image: url("./assets/limes.jpg");
  height: 100vh;
  margin: 0;
}
* {
  margin: 0;
  padding: 0;
}
</style>
