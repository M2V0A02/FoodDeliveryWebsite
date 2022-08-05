<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/food-watcher">food-watcher</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style>

    nav {
      padding: 30px;
      display: flex;
      flex-wrap: wrap;
    }

    nav a {
      font-weight: bold;
      color: #2c3e50;
      margin: 0 15px;
    }

    nav a.router-link-exact-active {
      color: #42b983;
    }
</style>