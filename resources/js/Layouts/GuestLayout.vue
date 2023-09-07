<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center bg-gray-100" style="background-image: url('/images/bg-login.jpg');">
        <div class="flex justify-center">
            <div class="w-6/12 p-6 rounded-lg">
                <div class="w-full sm:max-w-md mt-6 px-6 py-4 bg-white shadow-md overflow-hidden sm:rounded-lg">
                    
                    <slot />
                </div>
            </div>
            <div class="w-full"></div>
        </div>
    </div>
</template>