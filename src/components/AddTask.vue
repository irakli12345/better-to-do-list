<template>
  <form @submit="console.log('booyaa')">
    <input type="text" placeholder="task name" />
    <textarea placeholder="describe your task"></textarea>
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
  }
};
</script>
<style></style>