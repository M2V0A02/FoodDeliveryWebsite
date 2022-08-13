<template>
    <div>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#Modal">
        <slot></slot>
    </button>
    </div>
    <!-- Модальное окно -->
    <div class="modal fade" id="Modal" tabindex="-1" aria-labelledby="ModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="ModalLabel">{{  title  }}</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Закрыть"></button>
                </div>
                <div class="modal-body">
                    <div class="d-flex justify-content-end align-items-center" v-for="food of contents" :key="food">
                        <p class="text-start flex-grow-1 p-0 m-0">{{  food['text']  }}</p> 
                        <button 
                            class="btn btn-danger pt-0 pb-0 ps-2 pe-2 ms-2"
                            @click="this.$emit('subtractCount', food['id']);"
                        >
                        - 
                        </button><br>
                    </div>
                    <div class="d-flex justify-content-end text-danger fs-5">
                        {{conclusionText}}
                    </div>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                    <button type="button" class="btn btn-primary">{{  buttonText  }}</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        title: String,
        contents: Object,
        buttonText: String,
        conclusionText: String,
    }
}
</script>

<style>

</style>