<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import SecondaryButton from '@/Components/SecondaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, useForm } from '@inertiajs/vue3';

const form = useForm({
    status: '',
    plate: '',
    client: '',
    category: '',
    model: '',
});

const submit = () => {
    form.post(route('rentcar.store'), {
        onSuccess: () => {
            form.reset();
        }
    });
};

const cancel = () => {
    history.back();
};
</script>

<template>
    <Head title="Register" />
    <AuthenticatedLayout>
        <div class="py-6">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6">Register a Vehicle</div>
                    <form @submit.prevent="submit">
                        <div class="p-6">
                            <div class="hide" id="status" value="ACTIVE"></div>
                            <div class="grid md:grid-cols-2 md:gap-6">
                                <div class="mb-4 w-full">
                                    <InputLabel for="plate" class="text-gray-700">Plate</InputLabel>
                                    <TextInput id="plate" v-model="form.plate"
                                        class="w-full bg-gray-200 rounded-md shadow-sm" />
                                    <InputError v-if="form.errors.plate" :message="form.errors.plate" />
                                </div>
                                <div class="mb-4 w-full">
                                    <InputLabel for="client" class="text-gray-700">Client</InputLabel>
                                    <TextInput id="client" v-model="form.client"
                                        class="w-full bg-gray-200 rounded-md shadow-sm" />
                                    <InputError v-if="form.errors.client" :message="form.errors.client" />
                                </div>
                            </div>
                            <div class="grid md:grid-cols-2 md:gap-6">
                                <div class="mb-4 w-full">
                                    <InputLabel for="category" class="text-gray-700">Category</InputLabel>
                                    <TextInput id="category" v-model="form.category"
                                        class="w-full bg-gray-200 rounded-md shadow-sm" />
                                    <InputError v-if="form.errors.category" :message="form.errors.category" />
                                </div>
                                <div class="mb-4 w-full">
                                    <InputLabel for="model" class="text-gray-700">Model</InputLabel>
                                    <TextInput id="model" v-model="form.model"
                                        class="w-full bg-gray-200 rounded-md shadow-sm" />
                                    <InputError v-if="form.errors.model" :message="form.errors.model" />
                                </div>
                            </div>
                            <div class="flex justify-end">
                                <SecondaryButton type="button" class="text-gray-500 mr-2" @click="cancel">Cancel</SecondaryButton>
                                <PrimaryButton :class="{ 'opacity-25': form.processing }" :disabled="form.processing">Register</PrimaryButton>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
</AuthenticatedLayout></template>
