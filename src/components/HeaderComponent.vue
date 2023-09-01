<script setup>

</script>


<template>
    <nav class="bg-gray-600 mb-5">
    <div class=" px-2 sm:px-6 lg:px-8">
        <div class="relative flex h-16 items-center justify-between">
        <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
            <div class="flex flex-shrink-0 items-center">
            <span class="text-white ">Ostad Blog API</span>
            </div>
        </div>

        <div class="sm:ml-6">
            <div class="flex space-x-4">
                <RouterLink to="/" class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Home</RouterLink>
                <RouterLink to="/about" class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">About</RouterLink>
                <RouterLink to="/contact" class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Contact</RouterLink>
            </div>
            </div>
        </div>
    </div>
    </nav>
</template>
