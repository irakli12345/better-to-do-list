<template>
  <form @submit.prevent="handleSubmit()">
    <label for="taskname">Task Name</label>
    <input type="text" id="taskname" />
    <label for="desc">Description of the Task</label>

    <textarea id="desc"></textarea>
    <button type="submit">Add Task</button>
  </form>
</template>
<script>
export default {
  name: "AddTask",
  data: function() {
    return {
      booyaa: true
    };
  },
  methods: {
    handleSubmit() {
      console.log("booyaa");
    }
  }
};
</script>
<style>
input,
textarea {
  border-radius: 1rem;
  border: 2px solid rgba(49, 73, 230, 0.9);
  padding: 0.5rem 1rem;
}
button {
  background-color: crimson;
  color: white;
  padding: 0.5rem 1rem;
  border-style: solid;
  border: 1px solid crimson;
  border-radius: 1rem;
  font-family: "Baloo 2";
  margin-bottom: 1rem;
}
button:hover {
  background-color: rgb(226, 36, 74);
}
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
form > * {
  width: 35%;
  margin-top: 1rem;
}
@media screen and (min-width: 1080px) {
  form > * {
    width: 20%;
  }
}
@media screen and (min-width: 720px) {
  form > * {
    width: 25%;
  }
}
</style>