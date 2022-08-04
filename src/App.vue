<template>
  <header class="row header">
    <navbar-vue class="col-sm-12 col-md-6"></navbar-vue>
    <div class="col-sm-12 col-md-6">
      <button class="btn btn-success">Регистрация</button>
      <button class="btn">Авторизация</button>
      <button class="btn">Выход</button>
      <p class="d-inline-block ms-2 me-2">Имя</p> 
    </div>
  </header>
  <router-view/>
</template>

<script>
import NavbarVue from './components/Navbar.vue'
export default {
  components:{
    NavbarVue
  }  
}

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

</style>
