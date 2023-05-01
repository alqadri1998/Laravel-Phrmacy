<template>
    <Modal :show="modelValue" maxWidth="sm">
        <div class="max-w-2xl p-6 mx-4 bg-white rounded-md">
            <div class="flex items-center justify-between">
                <h3 class="text-2xl">Delete Item ?</h3>
                <svg
                    @click="closeModal"
                    xmlns="http://www.w3.org/2000/svg"
                    class="w-8 h-8 text-red-900 cursor-pointer"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
                    />
                </svg>
            </div>
            <div class="mt-4">
                <p class="mb-4 text-sm">
                    Are you sure you want to delete this note?
                </p>
                <button
                    @click="deleteData"
                    class="px-6 py-2 text-indigo-100 bg-indigo-600 rounded"
                >
                    Delete
                </button>
                <button
                    @click="closeModal"
                    class="px-6 py-2 ml-2 text-red-800 border border-red-600 rounded"
                >
                    Cancel
                </button>
            </div>
        </div>
    </Modal>
</template>

<script setup>
import { ref } from "vue";
import Modal from "@/Components/Modal.vue";
import { useForm } from "@inertiajs/inertia-vue3";
const form = useForm();
const props = defineProps({
    modelValue: {
        type: Boolean,
        default: false,
    },
    id: {
        type: String,
        required: true,
    },
    route: {
        type: String,
        required: true,
    },
});

const emit = defineEmits(["update:modelValue"]);
const closeModal = () => {
    emit("update:modelValue", false);
};

const deleteData = () => {
    emit("update:modelValue", false);
    form.delete(route(props.route, props.id));
};
</script>

<style></style>
