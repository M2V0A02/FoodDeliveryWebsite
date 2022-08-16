<template>
    <div>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#Modal">
        {{nameButton}}
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
                    <slot></slot>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                    <button type="button" class="btn btn-primary" @click="this.$emit('click')">{{  nameButton  }}</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        title: String,
        buttonText: String,
        nameButton: String,
    }
}
</script>

<style>

</style>