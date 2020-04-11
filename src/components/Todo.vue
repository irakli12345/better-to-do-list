<template>
  <div class="todo">
    <div class="heading">
      <span @click="$emit('deleteTodo')">
        <i class="fas fa-minus-circle"></i>
      </span>
      <p>{{todo.taskName}}</p>
      <i class="far fa-calendar"></i>
    </div>
    <div class="description">
      {{todo.description}}
      <ul>
        <li v-for="bullet in todo.bullets" :key="bullet">- {{" " + bullet}}</li>
      </ul>
    </div>
  </div>
</template>


<script>
export default {
  name: "Todo",
  props: ["todo"],
  data: function() {
    return { subtasks: [] };
  }
};
</script>
<style>
h1 {
  font-size: 50px;
}
.todo {
  flex-basis: 80%;
  height: 22%;
  background-color: rgba(42, 70, 255, 0.5);
  border-radius: 2rem;
}
.fa-minus-circle {
  background: red;
  border-radius: 50%;
  border: 1px solid rgba(255, 0, 0, 0.63);
}
.fa-minus-circle:hover {
  background: red;
  border: 1px solid red;
}
.heading {
  padding: 0.3rem 1.5rem;
  height: 15%;
  display: flex;
  justify-content: space-between;
  font-weight: 500;
}
.heading p {
  font-size: 18px;
  font-weight: bold;
  color: white;
  overflow: hidden;
  max-height: 2rem;
  flex-grow: 4;
}
.description {
  margin: 1rem;
  height: 60%;
  font-weight: 400;
  color: white;
  font-size: 11px;
  overflow: hidden;
}
li > span {
  max-height: 50%;
}
.bullet-icon {
  font-size: 20px;
}
li {
  padding: 0;
}

@media screen and (min-width: 360px) {
  .todo {
    height: 22%;
    flex-basis: 60%;
  }
}
@media screen and (min-width: 720px) {
  .todo {
    height: 40%;
    flex-basis: 40%;
  }
  .description {
    font-size: 13px;
  }
}
@media screen and (min-width: 1080px) {
  .todo {
    height: 60%;
    flex-basis: 20%;
  }
}
</style>