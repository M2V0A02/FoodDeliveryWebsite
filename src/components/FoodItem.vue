<template>
  <div class="card col-lg-3 col-md-5 col-sm-10 me-4 mb-3 mt-3 pt-3">
    <img class="card-img-top" :src="food.img" alt="Title">
    <div class="card-body">
        <h4 class="card-title">{{ food.title }} <span class="badge bg-dark" v-if="food.count != 0">{{food.count}}</span></h4>
        <p class="card-text">{{ food.compound }} {{food.price}}₽</p>
        <button class="btn btn-success" @click="this.$emit('addCount', food.id);">+</button>
        <button class="btn btn-danger" v-if="food.count != 0" @click="this.$emit('subtractCount', food.id);">-</button>
    </div>
  </div>
</template>

<script>
export default {
    props:{
        food: {
            type: Object,
            require: true
        }
    },
}
</script>

<style>

</style>