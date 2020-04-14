<template>
  <div style="height: 100vh">
    <form @submit.prevent="handleSubmit">
      <label for="taskname" class="taskNameLabel">Task Name</label>
      <input type="text" id="taskname" v-model="todo.taskName" />
      <label for="desc" class="descLabel">Description of the Task</label>

      <textarea id="desc" v-model="todo.description"></textarea>
      <span class="bulletbutton" @click="showbulletinput = !showbulletinput">Add Bullet Points</span>
      <div class="bulletinput" v-if="showbulletinput">
        <input type="text" id="addbullet" v-model="bulletpoint" />
        <span
          :class="[todo.bullets.length == 3 ? 'disabled' : '', 'bulletbutton']"
          @click="addBulletpoint"
        >Add</span>
        <ul>
          <h3>Bullets added:</h3>
          <h3 v-show="todo.bullets.length == 3 ">Max 3 Bullets allowed</h3>
          <li v-for="(bullet, index) in todo.bullets" :key="bullet">
            <u>
              {{bullet}}
              <span @click="todo.bullets.splice(index, 1)">
                <i class="fas fa-minus"></i>
              </span>
            </u>
          </li>
        </ul>
      </div>
      <button type="submit">Add Task</button>
    </form>
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
      this.todo = { taskName: "", description: "", bullets: [] };
      this.bulletpoint = "";
    },
    addBulletpoint() {
      this.todo.bullets.push(this.bulletpoint);
    }
  }
};
</script>
<style>
.disabled {
  background-color: grey !important;
  pointer-events: none;
}
.taskNameLabel {
  border-radius: 1rem;
  background-color: rgba(255, 255, 255, 0.781);
}
.descLabel {
  border-radius: 1rem;
  background-color: rgba(255, 255, 255, 0.781);
}
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
ul {
  list-style: none;
}
.bulletbutton {
  background-color: rgb(64, 185, 64);
  border: none;
  width: 30%;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 1rem;
  font-family: "Baloo 2";
  margin-bottom: 1rem;
  margin-top: 1rem;
}
.bulletbutton:hover {
  background-color: rgb(5, 184, 5);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 1rem;
  font-family: "Baloo 2";
  margin-bottom: 1rem;
}
.bulletinput {
  max-height: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  overflow: hidden;
  align-items: center;
}
.bulletinput input {
  width: 80%;
}
.fa-minus {
  color: red;
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
  .bulletbutton {
    width: 10%;
  }
}
</style>