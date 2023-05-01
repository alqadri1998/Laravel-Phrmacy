<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, Link, useForm } from "@inertiajs/inertia-vue3";
import BackButton from "@/Components/BackButton.vue";
import InputError from "@/Components/InputError.vue";
import TextInput from "@/Components/forms/TextInput.vue";
import Label from "@/Components/forms/Label.vue";
const form = useForm({
    name: "",
    address: "",
    contact_no: "",
    email: "",
    status: false,
});
const submit = () => {
    form.post(route("supplier.store"));
};
</script>
<template>
    <Head title="Medicine Supplier Create" />
    <AuthenticatedLayout>
        <div
            class="w-full max-w-2xl bg-white border mx-auto my-5 border-gray-200 rounded-lg shadow-md sm:p-6 md:p-8 dark:bg-gray-800 dark:border-gray-700"
        >
            <form class="space-y-6" @submit.prevent="submit">
                <h5 class="text-xl font-medium text-gray-900 dark:text-white">
                    Create Medicine Supplier
                    <BackButton :url="route('supplier.index')" />
                </h5>
                <div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <Label value="Supplier Name" id="name" />

                            <TextInput
                                id="name"
                                type="text"
                                v-model="form.name"
                                required
                                autofocus
                                autocomplete="name"
                            />
                            <InputError
                                class="mt-2"
                                :message="form.errors.name"
                            />
                        </div>
                        <div>
                            <Label value="Contact No" id="contact_no" />

                            <TextInput
                                id="contact_no"
                                type="text"
                                v-model="form.contact_no"
                                required
                                autofocus
                                autocomplete="contact_no"
                            />
                            <InputError
                                class="mt-2"
                                :message="form.errors.contact_no"
                            />
                        </div>
                    </div>
                </div>
                <div>
                    <Label value="Address" id="address" />

                    <TextInput
                        id="address"
                        type="text"
                        v-model="form.address"
                        required
                        autofocus
                        autocomplete="address"
                    />
                    <InputError class="mt-2" :message="form.errors.address" />
                </div>
                <div>
                    <Label value="Email" id="email" />

                    <TextInput
                        id="email"
                        type="email"
                        v-model="form.email"
                        required
                        autofocus
                        autocomplete="email"
                    />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>

                <div class="flex items-start">
                    <div class="flex items-start">
                        <div class="flex items-center h-5">
                            <input
                                id="remember"
                                type="checkbox"
                                value=""
                                class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800"
                                v-model="form.status"
                            />
                        </div>

                        <Label
                            value="Publish"
                            id="remember"
                            customClass="ml-2"
                        />
                    </div>
                </div>
                <button
                    type="submit"
                    class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                    :class="{ 'opacity-25': form.processing }"
                    :disabled="form.processing"
                >
                    Create
                </button>
            </form>
        </div>
    </AuthenticatedLayout>
</template>
