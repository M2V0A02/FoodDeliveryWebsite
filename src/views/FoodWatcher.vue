<template>
  <div class="Food Watcher">
    <vue-select 
      :nameSelect="nameSelect"
      :options="selectOptions"
      v-model:selectValue="selectValue"
    ></vue-select>
    {{selectValue}}
  </div>
</template>

<script>
import VueSelect from "@/components/VueSelect"
export default {
  components: {
    VueSelect
  },
  data() {
    return {
      selectOptions: [
        {name: 'Сотрудники', value:"employees"},
        {name: 'Поставщики', value:"provider"},
        {name: 'Раздел-меню', value:"menu-section"},
        {name: 'Блюдо', value:"dish"},
        {name: 'Заказ', value:"order"}
      ],
      nameSelect: 'Выберите таблицу',
      selectValue: ''
    }
  }
}
</script>

<style>

</style>