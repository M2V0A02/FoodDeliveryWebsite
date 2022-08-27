<template>
  <header class="header row mt-4">
    <navbar-vue class="col justify-content-center"></navbar-vue>
  </header>
  <router-view/>
</template>
<script>
import NavbarVue from '@/components/VueNavbar.vue'

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
