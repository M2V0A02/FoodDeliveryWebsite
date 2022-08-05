<template>
    <div class="table">
        <table class="table">
            <thead>
                <tr>
                <th scope="col" v-for="key of getKey" :key="key">
                    {{  key  }}
                </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="line of date" :key="line.id">
                    <td v-for="key of line" :key="key">
                        {{  key  }}
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
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
                return Object.keys(this.date[0])
        }
    }
}
</script>

<style>

</style>