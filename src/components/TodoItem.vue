<template>
  <div class="item">
    <div>
      <input
        type="checkbox"
        :checked="data.completed"
        @change="handleClickChange"
      />
      <span
        @click="handleClickChange"
        class="item-title"
        :class="data.completed ? 'item-title-completed' : ''"
        >{{ data.title }}</span
      >
    </div>
    <button class="item-btn" @click="handleClickDelete">delete</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["data"],
  setup(props, context) {
    const handleClickChange = () => {
      context.emit("handleClickChange", props.data.id);
    };

    const handleClickDelete = () => {
      context.emit("handleClickDelete", props.data.id);
    };
    return {
      handleClickChange,
      handleClickDelete,
    };
  },
};
</script>

<style scope lang="css">
.item {
  display: flex;
  justify-content: space-between;
  padding: 10px 10px;
  background-color: #e6bbbb;
  margin: 10px 0;
  align-items: center;
  border-radius: 10px;
}

.item-title {
  font-size: 1.4rem;
  padding: 10px;
  cursor: pointer;
}

.item-title-completed {
  text-decoration: line-through;
}

.item-btn {
  border: none;
  padding: 8px;
  font-size: 1rem;
  border-radius: 4px;
  cursor: pointer;
}

.item-btn:hover {
  opacity: 0.7;
}
</style>
