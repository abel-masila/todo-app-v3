<template>
  <h3>Vue 3 todo app</h3>
  <form @submit.prevent="addNewTodo">
    <label>
      New Todo
    </label>
    <input name="newTodo" v-model="newTodo" />
    <button>New Todo</button>
  </form>
  <ul>
    <li v-for="(todo, index) in todos" :key="todo.id" class="todo">
      <h3 @click="toggleDone(todo)" :class="{ done: todo.done }">
        {{ todo.content }}
      </h3>
      <button @click="removeTodo(index)">Remove Todo</button>
    </li>
  </ul>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  setup() {
    const newTodo = ref("");
    const todos = ref([]);
    function addNewTodo() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newTodo.value,
      });
      newTodo.value = "";
    }
    function toggleDone(todo) {
      todo.done = !todo.done;
    }
    function removeTodo(index) {
      todos.value.splice(index, 1);
    }
    return {
      newTodo,
      todos,
      addNewTodo,
      toggleDone,
      removeTodo,
    };
  },
};
</script>

<style>
body {
  font-family: sans-serif;
  padding-top: 1em;
  padding-bottom: 1em;
  font-size: 2em;
  width: 80%;
  margin: 0 auto;
}
input,
textarea,
button,
p,
div,
section,
article,
select {
  display: "block";
  width: 100%;
  font-family: sans-serif;
  font-size: 1em;
  margin: 0.5em;
}
.todo {
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}
</style>
