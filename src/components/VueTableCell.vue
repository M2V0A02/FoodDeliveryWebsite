<template>
  <th class="th-cell" v-if="isThead">
    {{value}}
  </th>
  <td class="cell" v-else>
    <input class="form-input form-control" @blur="(event) => this.$emit('changeValue', event.target.value)" :value="value">
  </td>
</template>

<script>
export default {
    props:{
        value:[Number, String, Boolean],
        isThead:Boolean,
    },
}
</script>

<style>
  .th-cell{
    min-width: 75px;
    max-width: 300px;
    padding:0 25px;
  }
  .cell{
    border: none !important;
    padding: 0 !important;
    width: auto !important;
  }

  .form-input{
    
  }
</style>