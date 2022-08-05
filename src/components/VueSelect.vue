<template>
    <select 
        class="form-select"
        aria-label="Default select example"
        @change="(event) => this.$emit('update:selectValue', event.target.value)"
        v-model="selectValue"
    >
        <option selected value="">{{  nameSelect  }}</option>
        <option 
            v-for="option of options"
            :key="option.value"
            :value="option.value"
        >
            {{ option.name }}
        </option>
    </select>
</template>

<script>
export default {
    props: {
       options: {
            type: Object,
            required: true
       },
       selectValue: String,
       nameSelect: String
    }
}
</script>

<style>

</style>