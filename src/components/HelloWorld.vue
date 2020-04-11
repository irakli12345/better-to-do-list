<template>
  <div class="main">
    <div class="lead-text-wrapper">
      <h1 class="leading-text">{{ msg }}</h1>
    </div>
    <div class="todos">
      <Todo
        v-for="(todo, index) in todoList.slice((pageNumber * 4)-4, pageNumber * 4)"
        :key="todo.taskName"
        :todo="todo"
        @deleteTodo="todoList.splice(index, 1)"
      ></Todo>
    </div>
    <h1 style="color:red" v-if="runoutofpages">No more todos</h1>
    <div class="pagination">
      <span
        @click="prevPage"
        :class="[pageNumber == 1 ? 'disabled' : '' , 'prevpage']"
      >Previous Page</span>
      You're on Page {{pageNumber}}
      <span
        @click.prevent="nextPage"
        :class="[runoutofpages ? 'disabled' : '' , 'nextpage']"
      >Next Page</span>
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
      pageNumber: 1
    };
  },
  methods: {
    nextPage: function() {
      this.pageNumber++;
    },
    prevPage: function() {
      this.pageNumber--;
    }
  },
  computed: {
    runoutofpages: function() {
      return (
        this.todoList.slice(this.pageNumber * 4 - 4, this.pageNumber * 4)
          .length < 4
      );
    }
  },
  mounted: function() {
    fetch("http://localhost:3000/todos")
      .then(res => res.json())
      .then(data => (this.todoList = data));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.disabled {
  background-color: grey !important;
  pointer-events: none;
}
.leading-text {
  margin-top: 1rem;
  font-size: 16px;
  background-color: rgba(42, 70, 255, 0.75);
  color: white;
  padding: 0.5rem 2rem;
  display: inline-block;
  border-radius: 2rem;
  font-weight: 600;
}
.leading-text:hover {
  background-color: rgba(49, 73, 230, 0.9);
}
.todos {
  width: 90vw;
  height: 160vh;
  background-color: rgba(190, 248, 113, 0.5);
  margin: auto;
  margin-top: 2rem;
  border-radius: 4rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}
* {
  font-family: "Baloo 2";
}

.prevpage {
  background-color: rgba(30, 155, 117, 0.9);
  color: white;
  padding: 0.5rem;
  border-radius: 1rem;
  margin: 1rem;
  -moz-user-select: none;
  -webkit-user-select: none;
}
.nextpage {
  background-color: rgba(22, 189, 31, 0.9);
  color: white;
  padding: 0.5rem;
  border-radius: 1rem;
  margin: 1rem;
  -moz-user-select: none;
  -webkit-user-select: none;
}
.pagination {
  background-color: rgba(49, 73, 230, 0.9);
  color: white;
  padding: 1rem;
  border-radius: 1rem;
  margin: 2rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 70%;
  margin: auto;
}
@media screen and (min-width: 360px) {
  .todos {
    height: 125vh;
  }
}
@media screen and (min-width: 480px) {
  .pagination {
    background-color: rgba(49, 73, 230, 0.9);
    color: white;
    padding: 1rem;
    border-radius: 1rem;
    margin: 2rem auto;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
}
@media screen and (min-width: 720px) {
  .leading-text {
    font-size: 18px;
  }
  .todos {
    width: 80vw;
  }
  .todos {
    width: 90vw;
    height: 80vh;
    background-color: rgba(190, 248, 113, 0.5);
    margin: auto;
    margin-top: 2rem;
    border-radius: 4rem;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
}

@media screen and (min-width: 1080px) {
  .leading-text {
    font-size: 26px;
  }
}
</style>
