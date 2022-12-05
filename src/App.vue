<template>
  <div>
    <List :items="users" :fields="['username', 'name']">
      <template #item="{ item: user }">
        {{ user.name }} {{ user.username }}
      </template>
    </List>
    <List :items="todos" :fields="['title']">
      <template #item="{ item: todo }">
        <MyTodo :item="todo"></MyTodo>
      </template>
    </List>
  </div>
</template>

<script>
import { loadTodos, loadUsers } from "./api.js";
import List from "./components/List.vue";
import MyTodo from "./components/MyTodo.vue";
export default {
  name: "App",
  components: {
    List,
    MyTodo,
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
