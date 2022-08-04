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
  <food-list 
    :foods="foods" 
    @addCount="(id) => foods.find(food => food.id === id).count++"
    @subtractCount="(id) => foods.find(food => food.id === id).count--"
  >
  </food-list>
  <router-view/>
</template>

<script>
import NavbarVue from '@/components/Navbar.vue'
import FoodList from '@/components/FoodList.vue'
export default {
  components:{
    NavbarVue,
    FoodList,
},
  data() {
      return {
          foods: [
            {id: "1", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "1"},              
            {id: "2", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "3", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "4", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "5", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "6", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "7", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", title: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
          ]
        }
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
