<template>
  <div class="Food Watcher">
    <div class="ms-auto me-auto col-12 col-md-6">
      <vue-select
        class="mb-4"
        :nameSelect="'Выберите столбец'"
        :options="selectColumn"
        v-model:selectValue="selectValue"
      ></vue-select>
      <div class="input-group mb-3 col-6">
        <div class="input-group-prepend">
          <span class="input-group-text">Поиск</span>
        </div>
        <input v-model="searchQuery" type="text" class="form-control">
      </div>
    </div>
    <control-panel 
     :data="showEmployees"
     @addRow="data => employees.push(data)"
     @changeLine=""
     @deleteRows=" deleteRows => employees = employees.filter(item => !deleteRows.includes(item.id))"
    ></control-panel>
    <vue-pagination
      class="justify-content-center" 
      :totalPages="totalPages" 
      v-model:current-page="currentPage" 
    />
  </div>
</template>

<script>
import VueSelect from "@/components/VueSelect"
import VueTable from "@/components/VueTable"
import ControlPanel from "@/components/ControlPanel.vue";
import VuePagination from "@/components/VuePagination.vue";

export default {
  components: {
    VueSelect,
    VueTable,
    ControlPanel,
    VuePagination,
},
  data() {
    return {
      selectOptions: [
        {name: 'id', value:"employees"},
        {name: 'Поставщики', value:"provider"},
        {name: 'Раздел-меню', value:"menu-section"},
        {name: 'Блюдо', value:"dish"},
        {name: 'Заказ', value:"order"}
      ],
      limit: 5,
      searchQuery: '',
      currentPage: 1,
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
  },
  computed: {
    totalPages() {
      return Math.ceil(this.searchedData.length / this.limit);
    },
    showEmployees() {
      return this.searchedData.slice(this.limit * (this.currentPage - 1), this.limit * this.currentPage)
    },
    searchedData() {
      if (this.selectValue === '') return this.employees
      return this.employees
              .filter(item => 
                item[this.selectValue].toString()
                .toLowerCase()
                .includes(this.searchQuery)
                )
    },
    selectColumn() {
      let keys = Object.keys(this.employees[0])
      return keys.map(key => {return {value: key, name:key}})
    }
  }
}
</script>

<style>

</style>