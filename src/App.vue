<template>
  <header class="header row">
    <navbar-vue class="col-sm-12 col-md-6"></navbar-vue>
    <div class="user-panel col-sm-12 col-md-6 d-flex justify-content-end">
      <button class="btn btn-success">Регистрация</button>
      <button class="btn">Авторизация</button>
      <button class="btn">Выход</button>
      <p class="username d-inline-block">Имя</p> 
    </div>
  </header>
  <router-view/>
</template>
<script>
import NavbarVue from '@/components/Navbar.vue'

export default {
  components:{
    NavbarVue,
},
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
  .user-panel > *{
    margin-right: 10px;
  }


  .username {
    margin: 0.375em 0;
  }
</style>
