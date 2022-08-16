<template>
    <div class="table-wrapper overflow-auto">
        <table class="overflow-auto">
            <thead>
                <vue-table-line 
                :isThead="true"
                :addCheckBoxes="addCheckBoxes"
                :row="getKey"
                @deleteRows="this.$emit('deleteRows', rowsToDelete)"
            />
            </thead>
            <tbody>
                <vue-table-line
                 v-for="line of date"
                 :key="line.id"
                 :addCheckBoxes="addCheckBoxes"
                 :row="line"
                 @changeDeleteRow="changeDeleteRows"
                 @changeValue="(value, id, key) => date.map(item => item.id == id ? item[key] = value : item)"
                 />
            </tbody>
        </table>
    </div>
</template>

<script>
import VueTableLine from './VueTableLine.vue'
export default {
  components: { VueTableLine },
    props:{
        date: {
            type: Object,
            required: true,
            default: []
        },
        addCheckBoxes :{
            type: Boolean
        }
    },
    data(){
        return {
            rowsToDelete:[]
        }
    },
    computed:{
        getKey(){
            if (this.date.length > 0)
                return Object.keys(this.date[0])
        }
    },
    methods:{
        changeDeleteRows(id){
            this.rowsToDelete.indexOf(id) == -1 ?
             this.rowsToDelete.push(id) :
              this.rowsToDelete = this.rowsToDelete.filter(idInArray => idInArray != id)
        }
    }
}
</script>

<style>
    .table-wrapper{
    }
</style>