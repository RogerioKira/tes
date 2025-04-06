<script setup>
const emit = defineEmits(emitOptions:['search']);

const search = (e) =>{
    emit('search', e.target.valeu);
};
</script>
<template>
    <form class="py-3 px-4 flex items-center">
        <label class="sr-only">Search</label>
        <div class="relative w-full">
            <input type="text" @input="search" placeholder="Pesquisar" class="bg-gray-50 border border-gray-300 text-gray-900 focus:outline">
        </div>
    </form>
</template>