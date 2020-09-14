<template>
  <li v-bind:class="{ done: todo.completed }">
    <input v-bind:checked="todo.completed" type="checkbox" @change="onChange" />
    <label>{{ todo.title }}</label>
    <button @click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo_prop: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      todo: this.todo_prop
    };
  },
  methods: {
    onChange() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 0.9rem;
}
input {
  margin: 0 0.5rem 0 0;
}
label {
  flex: 1;
}

.done {
  text-decoration: line-through;
}
</style>
