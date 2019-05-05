<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <input class="mark" type="checkbox" v-on:change="markComplete">
    <p>{{todo.title}}</p>
    <button @click="$emit('del-todo', todo.id )" class="del">X</button>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>
<style>
.is-complete {
  text-decoration: line-through;
}
.todo-item {
  background-color: #eff5f1;
  border-bottom: 1px solid #6af9ff;
  padding: 13px 30px;
  display: flex;
  justify-content: space-between;
}
.mark {
  display: inline-block;
}
.del {
  color: red;
  border-radius: 50%;
  height: 25px;
  width: 25px;
  text-align: center;
}
.del:focus {
  outline: none;
  background-color: rgb(226, 193, 193);
  color: #fff;
  border: 0;
}
</style>
