<template>
    <div>
        <v-checkbox :label="props.label"></v-checkbox>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    label: {
        required: true,
        type: String
    }
})
</script>

<style scoped>
</style>