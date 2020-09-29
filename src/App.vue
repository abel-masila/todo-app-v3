<template>
  <h3>Vue 3 todo app</h3>
  <form @submit.prevent="addNewTodo">
    <label>
      New Todo
    </label>
    <input name="newTodo" v-model="newTodo" />
    <button>New Todo</button>
  </form>
  <h3>{{ newTodo }}</h3>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  setup() {
    const newTodo = ref("");
    function addNewTodo() {
      console.log("submitted form");
    }
    return {
      newTodo,
      addNewTodo,
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
