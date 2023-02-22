<template>
  <add-todo :data="todoList" @add-todo="handleAddTodo" />
  <todo-item
    v-for="todo in todoList"
    :key="todo.id"
    :data="todo"
    @handleClickChange="handleClickChange"
    @handleClickDelete="handleClickDelete"
  />
</template>

<script>
import TodoItem from "./TodoItem";
import AddTodo from "./AddTodo";
import { ref } from "vue";

export default {
  name: "TodoList",
  components: {
    TodoItem,
    AddTodo,
  },
  setup() {
    const todoList = ref([
      {
        id: 1,
        title: "Cong viec 1",
        completed: false,
      },
      {
        id: 2,
        title: "Cong viec 2",
        completed: false,
      },
      {
        id: 3,
        title: "Cong viec 3",
        completed: false,
      },
    ]);

    const handleClickChange = (_id) => {
      todoList.value = todoList.value.map((todo) => {
        if (todo.id == _id) todo.completed = !todo.completed;
        return todo;
      });
    };

    const handleClickDelete = (_id) => {
      todoList.value = todoList.value.filter((todo) => {
        return todo.id != _id;
      });
      console.log(todoList.value);
    };

    const handleAddTodo = (newTodo) => {
      todoList.value.push(newTodo);
    };

    return {
      todoList,
      handleClickChange,
      handleClickDelete,
      handleAddTodo,
    };
  },
};
</script>

<style></style>
