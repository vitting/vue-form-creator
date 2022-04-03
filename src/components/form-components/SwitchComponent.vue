<template>
    <div>
        <v-switch :label="props.label"></v-switch>
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