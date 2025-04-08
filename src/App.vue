<template lang="pug">
  div
    TodoApp(msg="To-Do List")
</template>

<script>
import TodoApp from "./components/TodoApp.vue";

export default {
  name: "App",
  components: {
    TodoApp,
  },
};
</script>
