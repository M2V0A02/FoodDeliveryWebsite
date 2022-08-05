<template>
  <div class="home">
    <food-list 
      :foods="foods" 
      @addCount="(id) => foods.find(food => food.id === id).count++ "
      @subtractCount="(id) => foods.find(food => food.id === id).count--" 
    >
    </food-list>
    <modal-window 
      :title="titleModal"
      :contents="createOrder"
      :conclusionText="totalOrderPrice"
      :buttonText="buttonTextModal">Модальное окно</modal-window>
  </div>
</template>

<script>
// @ is an alias to /src
import FoodList from '@/components/FoodList.vue'
import ModalWindow from '@/components/ModalWindow.vue'

export default {
  name: 'HomeView',
  components: {
    FoodList,
    ModalWindow
  },
  data() {
      return {
          foods: [
            {id: "1", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "2", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "3", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "4", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "5", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "6", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "8", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "9", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
          ],
          titleModal: "Заказы",
          textModal: "Бургеры",
          buttonTextModal: "Сделать заказ",
        }
  },
  computed: {
    orderFoods() {
      return this.foods.filter(food => food.count > 0);
    },
    createOrder() {
      return this.orderFoods
        .map((item) => `Название - ${item['name']}, Количество - ${ item['count']}, цена: ${item['price']}, итого: ${item['count'] * item['price']}₽`)  
    },
    totalOrderPrice() {
      return this.orderFoods
        .reduce(function(sum, current) {
          return sum + current['price'] * current['count']
        }, 0) + "₽"
    }
  }
}
</script>
