<script setup>
import { ref } from "vue";
import NavBar from "@/Components/partials/NavBar.vue";
import AsideBar from "@/Components/partials/AsideBar.vue";
import NavLink from "@/Components/NavLink.vue";

const showingNavigationDropdown = ref(false);
</script>

<template>
    <!-- component -->
    <!-- This is an example component -->
    <div>
        <NavBar v-model="showingNavigationDropdown" />

        <div class="flex overflow-hidden bg-white pt-16">
            <AsideBar :showingNavigationDropdown="showingNavigationDropdown" />
            <div class="bg-gray-900 opacity-50 hidden fixed inset-0 z-10" id="sidebarBackdrop"></div>
            <div id="main-content" class="h-full w-full bg-gray-50 relative overflow-y-auto lg:ml-64">
                <main>
                    <slot />
                </main>
                <p class="text-center text-sm text-gray-500 my-10">
                    &copy; 2019-2021
                    <a href="#" class="hover:underline" target="_blank">Themesberg</a>. All rights reserved.
                </p>
            </div>
        </div>
    </div>
</template>
