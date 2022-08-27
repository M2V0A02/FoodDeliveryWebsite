<template lang="">
    <div>
     <modal-window
     :title="'Добавить строку'"
     :nameButton="'Добавить строку'"
     @click="addRow"
     >
     <div class="input-group mb-3" v-for="key of getKeys" ::key="key">
        <span class="input-group-text">{{  key  }}</span>
        <input type="text" :id="`${key}Form`" class="form-control" aria-label="Username" >
    </div>
     </modal-window>
     <vue-table
        class="d-flex justify-content-center" 
        :data="data"
        :addCheckBoxes="true"
        @deleteRows=" deleteRows => this.$emit('deleteRows', deleteRows)"
        @changeValue="(value, id, key) => data.map(item => item.id == id ? item[key] = value : item)"
    />
    </div>
</template>

<script>
import ModalWindow from './ModalWindow.vue';
import VueTable from './VueTable.vue';
export default {
    components:{
        ModalWindow,
        VueTable,
    },
    props:{
        data:Object,
    },
    computed:{
        getKeys(){
            if (this.data.length > 0)
                return Object.keys(this.data[0]).filter(item => item != 'id')
        }
    },
    methods:{
        addRow(){
            let obj = {}
            obj.id = Math.floor(Math.random() * 1000000)
            this.getKeys.forEach(item => obj[item] = this.$el.querySelector(`#${item}Form`).value)
            this.$emit('addRow', obj)
        }
    }
}
</script>
<style lang="">
    
</style>