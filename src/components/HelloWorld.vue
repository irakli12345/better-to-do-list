<template>
  <div class="main">
    <div class="lead-text-wrapper">
      <h1 class="leading-text">{{ msg }}</h1>
    </div>
    <div class="todos"></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
}
.leading-text {
  margin-top: 1rem;
  font-size: 16px;
  background-color: rgba(42, 70, 255, 0.75);
  color: white;
  padding: 0.5rem 2rem;
  display: inline-block;
  border-radius: 2rem;
}
.leading-text:hover {
  background-color: rgba(49, 73, 230, 0.9);
}
.todos {
  width: 90vw;
  height: 60vh;
  background-color: rgba(190, 248, 113, 0.5);
  margin: auto;
  margin-top: 2rem;
  border-radius: 4rem;
}
@media screen and (min-width: 720px) {
  .leading-text {
    font-size: 18px;
  }
  .todos {
    width: 80vw;
  }
}

@media screen and (min-width: 1080px) {
  .leading-text {
    font-size: 26px;
  }
}
</style>
