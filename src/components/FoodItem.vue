<template>
  <div class="card col-lg-3 col-md-5 col-sm-6 col-sm-9 col-10 me-2 mb-2 mt-1 pt-3">
    <img class="card-img-top" :src="food.img" alt="Title">
    <div class="card-body">
      <h4 class="card-title">{{ food.name }}</h4>
      <h4>
        <span class="badge bg-dark" v-if="food.count != 0">{{food.count}}</span>  
      </h4>
      <p class="card-text">{{ food.compound }}</p>
      </div>
    <div class="card-footer text-muted">
        <button class="btn btn-success" @click="this.$emit('addCount', food.id);">+</button>
        <button class="btn btn-danger" v-if="food.count != 0" @click="this.$emit('subtractCount', food.id);">-</button>
        <div class="mt-2">
          {{food.price}}₽
        </div>
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