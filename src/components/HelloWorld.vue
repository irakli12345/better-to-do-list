<template>
  <div class="main">
    <div class="lead-text-wrapper">
      <h1 class="leading-text">{{ msg }}</h1>
    </div>
    <div class="todos">
      <div class="todo">
        <div class="heading">
          <i class="fas fa-minus-circle"></i>
          <p>bla bla bla heading title</p>
          <i class="far fa-calendar"></i>
        </div>
      </div>
      <div class="todo"></div>
    </div>
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
  display: flex;
  justify-content: space-around;
  align-items: center;
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
