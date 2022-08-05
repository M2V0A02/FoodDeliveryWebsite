<template>
  <div class="Food Watcher">
    <vue-select 
      :nameSelect="nameSelect"
      :options="selectOptions"
      v-model:selectValue="selectValue"
    ></vue-select>
    <vue-table :date="employees"/>
  </div>
</template>

<script>
import VueSelect from "@/components/VueSelect"
import VueTable from "@/components/VueTable"

export default {
  components: {
    VueSelect,
    VueTable
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
      selectValue: '',
      employees: [
        {
          id: new Date(),
          name: "Egor"
        },
        {
          id: new Date(),
          name: "Egor"
        },
        {
          id: new Date(),
          name: "Egor"
        },
        {
          id: new Date(),
          name: "Egor"
        },
        {
          id: new Date(),
          name: "Egor"
        },
        {
          id: new Date(),
          name: "Egor"
        }
      ]
    }
  }
}
</script>

<style>

</style>