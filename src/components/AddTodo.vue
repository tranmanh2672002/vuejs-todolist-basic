<template>
  <div class="addTodo">
    <input
      class="input"
      type="text"
      placeholder="Add todo ..."
      spellcheck="false"
      v-model="input"
    />
    <button class="addTodo-btn" @click="handleClickAdd">Add</button>
  </div>
</template>

<script>
import { ref } from "vue";
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  props: ["data"],
  setup(props, context) {
    const input = ref("");

    const handleClickAdd = () => {
      const title = input.value;
      if (title == "") return;
      const newTodo = {
        id: uuidv4(),
        title: title,
        completed: false,
      };
      context.emit("add-todo", newTodo);
      input.value = "";
    };

    return {
      input,
      handleClickAdd,
    };
  },
};
</script>

<style scope>
.addTodo {
  padding: 10px;
  background-color: beige;
  display: flex;
  align-items: center;
  justify-content: center;
}

.input {
  border: none;
  padding: 10px;
  outline: none;
  border-radius: 4px;
  margin-right: 10px;
  font-size: 1.2rem;
  width: 300px;
}

.addTodo-btn {
  border: none;
  border-radius: 4px;
  background-color: rgb(142, 142, 241);
  padding: 10px;
  outline: none;
  font-size: 1.2rem;
}

.addTodo-btn:hover {
  background-color: rgb(120, 120, 240);
}
</style>
