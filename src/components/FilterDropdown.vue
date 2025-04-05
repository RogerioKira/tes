<script setup>
import {ref} from "vue";
const show = ref(valeu:false);
const props = defineProps(props{
    items:{
        type:Array,
        required:true,
    }
});

const emit = defineEmits(emitOptions: ['filter']);

const statuses =computed(getter() => {
    return [...new Set(props.items.map(item => Status))];
});
const filter = (e) =>{
    emit('filter', e.target.value);
}
</script>
<template>
    <div class="relative flex items-center w-full px-4">
        <button  @click="show = !show"class="w-full flex items-center justify-center py-2 px-4 text-sm font-medium text-gray-900 focus:outline">
            Filter 
        </button>
        <div v-if="show" class="absolute top-12 right-0 z-10 w-48 p-3 bg-white rounded-lg shadow">//
            <h6 class="mb-3 text-sm font-medium text-gray-900">Status</h6>
            <ul class="space-y-2 text-s">
                <li v-for="(status,index) in statuses">
                    <input :id="filter_option_${index}" @change="filter" type="checkbox" :value="status" class="w-3 h4 bg-gray-100 border-gray-300 rounde text">
                    <label :for="filter_option_${index}" class="ml-2 twxt-sm font-medium text-gray-900">({status})</label>
                </li>
            </ul>
        </div>
    </div>
    
</template>