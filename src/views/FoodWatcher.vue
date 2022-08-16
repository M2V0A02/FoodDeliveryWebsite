<template>
  <div class="Food Watcher">
    <!-- <vue-select 
      :nameSelect="nameSelect"
      :options="selectOptions"
      v-model:selectValue="selectValue"
    ></vue-select> -->
    <control-panel 
     :data="employees"
     @addRow="data => employees.push(data)"
     @changeLine=""
     @deleteRows=" deleteRows => employees = employees.filter(item => !deleteRows.includes(item.id))"
    ></control-panel>
  </div>
</template>

<script>
import VueSelect from "@/components/VueSelect"
import VueTable from "@/components/VueTable"
import ControlPanel from "@/components/ControlPanel.vue";

export default {
  components: {
    VueSelect,
    VueTable,
    ControlPanel
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
          id: 1,
          name: "Egor",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        },
        {
          id: 2,
          name: "Egor",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        },
        {
          id: 3,
          name: "Egor",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        },
        {
          id: 4,
          name: "Egor",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        },
        {
          id: 5,
          name: "Egor",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        },
        {
          id: 6,
          name: "EgorEEg",
          pass: '123',
          gender: 'm',
          sex: 'm',
          value: 5000,
          isMarried: false,
          isGenius: true,
        }
      ],
    }
  }
}
</script>

<style>

</style>