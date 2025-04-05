<script setup>
import DataTable from ".components/DataTable.vue";
import {onMounted} from "vue";

const items = ref(values:[]);

onMounted(hook: async() => {
  const response = await fetch (input: 'http://localhost:8080/api/task');
  items.value = await response.json();
});
</script>
<template>
  <div class="p-8 bg-gray-100 min-h-screen">
    <DataTable items="items"/>
  </div>
</script>
