<template>
  <ul>
    <TodoItem
      v-for="todo_prop of todos"
      :key="todo_prop.id"
      v-bind:todo_prop="todo_prop"
      @remove-todo="removeTodo"
    />
  </ul>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "todolist",
  props: ["todos"],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    }
  }
};
</script>

<style scoped>
ul {
  margin: 0 auto;
  padding: 0;
  max-width: 600px;
  width: 100%;
  list-style: none;
}
</style>
