<template>
  <div id="app">
    <inputTodo></inputTodo>
    <tableTodo :todos="tasks"></tableTodo>
  </div>
</template>

<script>
import inputTodo from "./components/inputTodo.vue";
import tableTodo from "./components/tableTodo.vue";

export default {
  name: "App",
  components: {
    inputTodo,
    tableTodo
  },
  data: function () {
    return {
      tasks: this.tasks,
    }
  }
};
</script>

<style>
</style>
