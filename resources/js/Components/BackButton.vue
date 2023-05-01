<script setup>
import { Link } from "@inertiajs/inertia-vue3";
import Icon from "@/Components/Icon.vue";
const props = defineProps({
    url: {
        type: String,
        default: () => ({}),
    },
});
</script>
<template>
    <Link
        :href="url"
        class="inline-flex bg-red-600 hover:bg-red-800 px-1 py-1 mx-2 my-2 rounded-md text-white font-semibold tracking-wide cursor-pointer"
    >
        <Icon path="M9 15L3 9m0 0l6-6M3 9h12a6 6 0 010 12h-3" />
    </Link>
</template>

<style></style>
