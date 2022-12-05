<template>
  <List :items="users" :fields="['username', 'name']" />
</template>

<script>
import { loadTodos, loadUsers } from "./api.js";
import List from "./components/List.vue";

export default {
  name: "App",
  components: {
    List,
  },
  data() {
    return {
      users: [],
      todos: [],
    };
  },
  mounted() {
    loadUsers().then((users) => {
      this.users = users;
    });
    loadTodos().then((todos) => {
      this.todos = todos;
    });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
