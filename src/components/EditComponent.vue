<template>
    <div class="d-flex">
        <slot></slot>
        <v-btn v-if="showEdit" class="ml-2" icon="mdi-pencil" color="primary" size="x-small"></v-btn>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    showEdit: {
        type: Boolean, 
        required: false,
        default: false
    }
})
</script>

<style scoped>
</style>