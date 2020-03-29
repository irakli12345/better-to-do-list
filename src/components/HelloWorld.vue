<template>
  <div class="main">
    <div class="lead-text-wrapper">
      <h1 class="leading-text">{{ msg }}</h1>
    </div>
    <div class="todos">
      <Todo v-for="movie in movieList" :key="movie.title" :movie="movie"></Todo>
    </div>
    <AddTask></AddTask>
  </div>
</template>

<script>
import Todo from "./Todo";
import AddTask from "./AddTask";
export default {
  components: { Todo, AddTask },
  name: "HelloWorld",
  props: {
    msg: String
  },
  data: function() {
    return {
      todoList: [],
      movieList: []
    };
  },
  mounted: function() {
    fetch("http://localhost:3000/movies")
      .then(res => res.json())
      .then(data => (this.movieList = data));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
  display: flex;
  justify-content: space-around;
  align-items: center;
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
