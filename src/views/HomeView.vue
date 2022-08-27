<template>
  <div class="home">
    <food-list
      :foods="showFood" 
      @addCount="(id) => foods.find(food => food.id === id).count++ "
      @subtractCount="(id) => foods.find(food => food.id === id).count--" 
    >
    </food-list>
    <div class="">
      <pagination
        class="justify-content-center" 
        :totalPages="totalPages" 
        v-model:current-page="currentPage">
        <a href="#1"></a>
      </pagination>
    </div>
    <div class="row me-4 mb-4"  >
      <modal-window
        :title="'Заказы'"
        :nameButton="'Сделать заказ'"
      >
      <div>
         <div class="d-flex justify-content-end align-items-center" v-for="food of createOrder" :key="food">
          <p class="text-start flex-grow-1 p-0 m-0">{{  food['text']  }}</p> 
          <button 
              class="btn btn-danger pt-0 pb-0 ps-2 pe-2 ms-2"
              @click="() => foods.find(item => item.id === food['id']).count--"
          >
          - 
          </button><br>
        </div>
        <div class="d-flex justify-content-end text-danger fs-5">
            {{totalOrderPrice}}
        </div>
      </div>
      </modal-window>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import FoodList from '@/components/FoodList.vue'
import ModalWindow from '@/components/ModalWindow.vue'
import Pagination from '@/components/VuePagination.vue'

export default {
  name: 'HomeView',
  components: {
    FoodList,
    ModalWindow,
    Pagination
  },
  data() {
      return {
          foods: [
            {id: "1", img: "https://img1.russianfood.com/dycontent/images_upl/64/sm_63397.jpg", name: "Борщ с говядиной", compound: "говядина, свекла, картофель,", price: "250", count: "0"},              
            {id: "2", img: "https://img1.russianfood.com/dycontent/images_upl/66/sm_65699.jpg", name: "Борщ классический", compound: "говядина, вода, картофель", price: "200", count: "0"},              
            {id: "3", img: "https://img1.russianfood.com/dycontent/images_upl/124/sm_123024.jpg", name: "Борщ на курином бульоне", compound: "курица, капуста, свекла", price: "180", count: "0"},              
            {id: "4", img: "https://img1.russianfood.com/dycontent/images_upl/256/sm_255825.jpg", name: "Красный борщ", compound: "мясо, морковь, лук репчатый", price: "270", count: "0"},              
            {id: "5", img: "https://img1.russianfood.com/dycontent/images_upl/180/sm_179842.jpg", name: "Борщ Традиционный", compound: "говядина, картофель, морковь", price: "220", count: "0"},              
            {id: "6", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "8", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "9", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "11", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "12", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "13", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "14", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "15", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Дорогой бургер", compound: "Мясо, хлеб, майонез", price: "240", count: "0"},              
            {id: "16", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "18", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "19", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},
            {id: "21", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "22", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Плохой бургер", compound: "Мясо, хлеб, майонез", price: "50", count: "0"},              
            {id: "23", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "24", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "25", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "26", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "28", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "29", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},
            {id: "31", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "32", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Элитный бургер", compound: "Мясо, хлеб, майонез", price: "680", count: "0"},              
            {id: "33", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "34", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "35", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "36", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "38", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "Бургер", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},              
            {id: "39", img: "https://piginfo.ru/upload/iblock/c13/burger.jpg", name: "П", compound: "Мясо, хлеб, майонез", price: "120", count: "0"},
          ],
          textModal: "Бургеры",
          currentPage: 1,
          limit: 6,
        }
  },
  computed: {
    orderFoods() {
      return this.foods.filter(food => food.count > 0);
    },
    createOrder() {
      return this.orderFoods
        .map((item) => {
          return {
            id: item['id'],
            text: `Название - ${item['name']}, Количество - ${ item['count']},
            цена: ${item['price']}, итого: ${item['count'] * item['price']}₽` 
          }         
        });    
    },
    totalOrderPrice() {
      return this.orderFoods
        .reduce(function(sum, current) {
          return sum + current['price'] * current['count']
        }, 0) + "₽"
    },
    showFood() {
      return this.foods.slice(this.limit * (this.currentPage - 1), this.limit * this.currentPage)
    },
    totalPages() {
      return Math.ceil(this.foods.length / this.limit);
    }
  },
}
</script>

<style>
  .modal-text{
    padding: 5px;
    margin: 5px
  }
</style>