<template>
    <tr>
      <th v-if="isThead && addCheckBoxes">
        <button class="btn btn-danger" @click="this.$emit('deleteRows')"> Удалить</button>
      </th>
      <th v-else-if="addCheckBoxes">
        <input type="checkbox" 
         class="table-checkbox"
         @change="this.$emit('changeDeleteRow', row.id)">
        <label for="checkbox"></label>
      </th>
      <vue-table-cell
        v-for="(cell, key) in row"
        :isThead="isThead"
        :key="key"
        :value="cell"
        @changeValue=" (value) => this.$emit('changeDeleteRow', value, row.id, key)"
      />
    </tr>
</template>

<script>
import VueTableCell from '@/components/VueTableCell.vue'
export default {
    components: { VueTableCell },
    props: {
        row:Object,
        addCheckBoxes: {
          type: Boolean
        },
        isThead: {
          type: Boolean,
          default: false
        }
    },
}
</script>

<style>
  .table-checkbox{
    width: 25px;
    height: 25px;
  }
</style>