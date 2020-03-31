<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label for="taskname">Task Name</label>
      <input type="text" id="taskname" v-model="todo.taskName" />
      <label for="desc">Description of the Task</label>

      <textarea id="desc" v-model="todo.description"></textarea>
      <button class="bulletbutton" @click="showbulletinput = !showbulletinput">Add Bullet Points</button>
      <div v-if="showbulletinput">
        <input type="text" id="addbullet" v-model="bulletpoint" />
        <button
          class="bulletbutton"
          style="width: 20%; margin-left: 1rem"
          @click="addBulletpoint"
        >Add</button>
        <ul>
          <h3>Bullets added:</h3>
          <li v-for="bullet in todo.bullets" :key="bullet">
            <u>{{bullet}}</u>
          </li>
        </ul>
      </div>
      <button type="submit">Add Task</button>
    </form>
    <div v-if="showtask">
      <h1>{{todo.taskName}}</h1>
      <h1>{{todo.description}}</h1>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddTask",
  data: function() {
    return {
      todo: {
        taskName: "",
        description: "",
        bullets: []
      },
      showbulletinput: false,
      bulletpoint: ""
    };
  },
  methods: {
    handleSubmit() {
      fetch("http://localhost:3000/todos", {
        method: "POST",
        headers: {
          Accept: "application/json, text/plain, */*",
          "Content-type": "application/json"
        },
        body: JSON.stringify(this.todo)
      });
    },
    addBulletpoint() {
      this.todo.bullets.push(this.bulletpoint);
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

.bulletbutton {
  background-color: rgb(64, 185, 64);
  border: none;
  width: 10%;
}
.bulletbutton:hover {
  background-color: rgb(5, 184, 5);
}
ul {
  list-style: none;
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