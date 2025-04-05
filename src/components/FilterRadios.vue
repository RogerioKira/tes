<script setup>
const emit = defineEmits(emitOptions:['filter']);

const filter = (e) => {
    emit(event: 'filter', e.target.value);
}
</script>

<template>
    <label class="flex mr-4 items-center flex-nowrap">
        <input type="radio" name = "show" value="all" checked @change="filter">
        <span class="whitespace-nowrap ml-1">Show all</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
        <input type="radio" name = "show" value="today" checked @change="filter">
        <span class="whitespace-nowrap ml-1">Due Today</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
        <input type="radio" name = "show" value="past" checked @change="filter">
        <span class="whitespace-nowrap ml-1">Past Due</span>
    </label>

</template>