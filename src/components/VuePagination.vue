<template>
    <nav aria-label="Page navigation example">
        <ul class="pagination">
            <li 
                class="page-item"
                @click.prevent="currentPage <= 1 ? currentPage = totalPages : currentPage--"
            >
                <a class="page-link" href="#">Предыдущая</a>
            </li>
            <li 
                class="page-item" 
                v-for="page of totalPages" 
                :key="page"
                v-bind:class="{active: page == currentPage}" 
                @click.prevent=" currentPage = page"
            >
                <a class="page-link" href="#">{{  page  }}</a>
            </li>
            <li 
                class="page-item"
                @click.prevent="currentPage >= totalPages ? currentPage = 1 : currentPage++"
            >
                <a class="page-link" href="#">Следующая</a>
            </li>
        </ul>   
    </nav>
</template>

<script>
export default {
    props:{
        totalPages: Number,
        currentPage: Number
    },
    watch:{
        currentPage(){
            this.$emit('update:currentPage', this.currentPage)
        }
    }
}
</script>

<style>
    nav{
        padding-top:0px;
    }
</style>