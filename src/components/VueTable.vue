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
                 v-for="line of data"
                 :key="line.id"
                 :addCheckBoxes="addCheckBoxes"
                 :row="line"
                 @changeDeleteRow="changeDeleteRows"
                 @changeValue="(value, id, key) => this.$emit('changeValue', value, id, key)"
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
        data: {
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
            if (this.data.length > 0)
                return Object.keys(this.data[0])
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