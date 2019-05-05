<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>
<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";

import axios from "axios";

const URL = "https://jsonplaceholder.typicode.com/todos";
const LIMIT = "?_limit=5";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(URL + `/${id}`)
        .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => err);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post(URL, {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => err);
    }
  },
  created() {
    axios
      .get(URL + LIMIT)
      .then(res => (this.todos = res.data))
      .catch(error => error);
  }
};
</script>
<style>
</style>

