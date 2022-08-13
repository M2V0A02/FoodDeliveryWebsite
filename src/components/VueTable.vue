<template>
    <div class="table-wrapper overflow-auto">
        <table class="overflow-auto">
            <thead>
                <vue-table-line 
                :isThead="true"
                :row="getKey"
            />
            </thead>
            <tbody>
                <vue-table-line
                 v-for="line of date"
                 :key="line.id"
                 :row="line"
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
        }
    },
    computed:{
        getKey(){
            if (this.date.length > 0)
                return ['', ...Object.keys(this.date[0])]
        }
    }
}
</script>

<style>
    .table-wrapper{
    }
</style>