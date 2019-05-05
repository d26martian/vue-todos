<template>
  <div class="header">
    <h1 class="wrap">{{name}}</h1>
    <div class="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      name: "My tasks"
    };
  }
};
</script>
<style>
.header {
  background-color: #0c0c0c;
}
.wrap {
  color: #ccc;
  padding: 10px 0;
  margin: 0;
  text-align: center;
}
.nav {
  color: #fff;
  text-align: center;
}
.nav a {
  color: #fff;
  text-decoration: none;
  margin: 0 10px;
}
</style>

