<template>
  <div class="todo">
    <div class="heading">
      <i class="fas fa-minus-circle"></i>
      <p>{{movie.title}}</p>
      <i class="far fa-calendar"></i>
    </div>
  </div>
</template>


<script>
export default {
  name: "Todo",
  props: ["movie"],
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
  background: rgba(255, 0, 0, 0.63);
  border-radius: 50%;
  border: 1px solid rgba(255, 0, 0, 0.63);
}
.fa-minus-circle:hover {
  background: red;
  border: 1px solid red;
}
.heading {
  border-bottom: 2px solid red;
  padding: 0.3rem 1.5rem;
  max-height: 15%;
  display: flex;
  justify-content: space-between;
}
.heading p {
  font-size: 12px;
  font-weight: bold;
  color: white;
  max-width: 40%;
  overflow: hidden;
  max-height: 1rem;
}
</style>