<template>
  <div class="wrapper">
    <div class="header">Todo list</div>
    <AddTodo />
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.wrapper {
  padding: 40px 100px;
  background-color: #f2f9fa;
}

.header {
  background-color: #ccc;
  padding: 20px;
  font-size: 1.4rem;
  border-radius: 10px;
}
</style>
