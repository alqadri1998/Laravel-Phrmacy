<template>
    <nav
        class="flex justify-between items-center pt-4"
        aria-label="Table navigation"
    >
        <span class="text-sm font-normal text-gray-500 dark:text-gray-400"
            >Showing
            <span class="font-semibold text-gray-900 dark:text-white"
                >1-{{ data.to }}</span
            >
            of
            <span class="font-semibold text-gray-900 dark:text-white">{{
                data.total
            }}</span></span
        >
        <ul class="inline-flex items-center -space-x-px">
            <li v-for="(link, index) in data.links" :key="index">
                <Link
                    v-if="link.url"
                    :href="link.url"
                    class="block py-2 px-3 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white"
                    :class="{
                        'text-blue-600 bg-blue-50 border-blue-300 hover:bg-blue-100 hover:text-blue-700':
                            link.active,
                    }"
                    v-html="link.label"
                ></Link>
            </li>
        </ul>
    </nav>
</template>

<script setup>
import { Link } from "@inertiajs/inertia-vue3";
import { onMounted } from "vue";
defineProps({
    data: Object,
});
</script>
