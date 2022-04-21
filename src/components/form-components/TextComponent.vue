<template>
        <EditComponent :show-edit="!disabled">
            <v-text-field
                :label="props.label"
                :type="props.type"
                variant="outlined"
                density="compact"
                :disabled="props.disabled"
            ></v-text-field>
        </EditComponent>
</template>

<script setup lang="ts">
import EditComponent from "../EditComponent.vue";
const props = defineProps({
    label: {
        required: true,
        type: String
    },
    type: {
        required: true,
        type: String
    },
    disabled: {
        required: false,
        type: Boolean,
        default: false
    }
})
</script>

<style lang="scss" scoped>
</style>