<template>
    <tr>
      <th v-if="!isThead">
        <input type="checkbox" id="checkbox" >
        <label for="checkbox"></label>
      </th>
      <vue-table-cell
        v-for="(cell, key) in row"
        :isThead="isThead"
        :key="key"
        :value="cell"
        @changeValue=" (value) => this.$emit('changeValue', value, row.id, key)"
      />
    </tr>
</template>

<script>
import VueTableCell from '@/components/VueTableCell.vue'
export default {
    components: { VueTableCell },
    props: {
        row:Object,
        isThead: {
          type: Boolean,
          default: false
        }
    },
}
</script>

<style>

</style>