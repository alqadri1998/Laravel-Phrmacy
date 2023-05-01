<script setup>
defineProps(["value", "id", "customClass"]);
</script>

<template>
    <label
        :for="id"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        :class="customClass"
    >
        <span v-if="value">{{ value }}</span>
        <span v-else><slot /></span>
    </label>
</template>
