<template>
  <div class="food-list row justify-content-center">
    <food-item 
        v-for="food of foods" 
        :key="food.id" 
        :food="food" 
        @addCount="this.$emit('addCount', food.id)"
        @subtractCount="this.$emit('subtractCount', food.id)"
    >
    </food-item>
  </div>
</template>

<script>
import FoodItem from "@/components/FoodItem.vue"
export default {
    components: {
        FoodItem
    },
    props: {
        foods: {
            type: Object,
            required: true
        }
    },
    methods:{
        addCount(id){
            console.log(id)
        }
    }
}
</script>

<style>

</style>