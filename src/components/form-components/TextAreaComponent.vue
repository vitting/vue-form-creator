<template>
    <div>
        <v-textarea :label="props.label"></v-textarea>
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