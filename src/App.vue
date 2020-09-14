<template>
  <div class="text-center">
    <h1>Todo app</h1>
    <input placeholder="Добавить задачу" @keydown="addTodo" />
  </div>
  <hr />
  <TodoList v-bind:todos="todos" @remove-todo="removeTodo" />
</template>

<script>
import { TodoList } from "./components/";

export default {
  name: "app",
  data() {
    return {
      todos: [
        { id: 0, title: "Поработать", completed: false },
        { id: 1, title: "Пройти собеседование", completed: false },
        { id: 2, title: "Радоваться", completed: false }
      ]
    };
  },
  components: {
    TodoList
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(el => el.id != id);
    },
    addTodo(e) {
      if (e.key === "Enter" && e.target.value) {
        this.todos.push({
          completed: false,
          title: e.target.value,
          id: this.todos.length + 1
        });

        e.target.value = "";
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.text-center {
  text-align: center;
}
</style>
