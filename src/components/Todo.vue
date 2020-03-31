<template>
  <div class="todo">
    <div class="heading">
      <i class="fas fa-minus-circle"></i>
      <p>{{todo.taskName}}</p>
      <i class="far fa-calendar"></i>
    </div>
    <div class="description">{{todo.description}}</div>
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
  flex-basis: 40%;
  height: 60%;
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
}
.heading p {
  font-size: 18px;
  font-weight: bold;
  color: white;
  max-width: 40%;
  overflow: hidden;
  max-height: 2rem;
}
.description {
  border: 1px solid red;
  margin: 1rem;
  height: 60%;
  font-weight: bold;
  color: white;
}
</style>