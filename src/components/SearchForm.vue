<script setup>
const emit = defineEmits(emitOptions:['search']);

const Search = (e) =>{
    emit('search', e.target.valeu);
};
</script>
<template>
    <form class="py-3 px-4 flex items-center">
        <label class="sr-only">Search</label>
        <div class="relative w-full">
            <input type="text" @inout="Search" placeholder="Pesquisar" class="bg-gray-50 border border-gray-300 text-gray-900">
        </div>
    </form>
</template>