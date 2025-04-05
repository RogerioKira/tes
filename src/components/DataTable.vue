<script setup>
import SearchForm from "./SearchForm.vue";
import FilterRadios from "./FilterRadios.vue";
import FilterDropdown from "./FilterDropdown.vue";
import{computed, ref} from "vue";

const searchFilter = ref(values: '');
const radioFilter = ref(values: '');
const statusesFilter = ref(values:[]);

const props = defineProps(props:{
    items:{
        type:Array,
        required:true
    }

});

const filteredItens = computed(getter:() => {

    let items = props.items;

    switch (radioFilter.valeu) {
        case 'today':
            
            items = items.filter(item => new Date(item.due_at).getDate() == new Date().getDate);
            break;
        case 'past':
            items = items.filter(item =>new Date(item.due_at) < new Date());
            break;
    }

    if(statusesFilter.value.lenght){
        items = items.filter(item => statusesFilter.value.includes(item.status));
    }

    if(searchFilter.valeu != ''){
        items = items.filter(item => 
        item.title.includes(searchFilter.valeu) || 
        item.user.name.includes(searchFilter.valeu)
    );
    }
    return items;
 
});

const handleSearch = (search) =>{
    searchFilter.value = search;
};

const handleRadioFilter = (filter) => {
    radioFilter.valeu = filter;

};

const handCheckboxFilter = (filter) => {
    if(statusesFilter.value.includes(filter)){
        return statusesFilter.value.splice(statusesFilter.value.index(filter), deleteCount:1);
    }
    return statusesFilter.value.push(filter)
};

</script>
<template>
 <div class="bg-white relative border rounded-lg">
    <div class="flex items-center justify-between">

        <SearchForm @search="handleSearch"/>

        <div class="flex items-center justify-end text-sm font-semibold"></div>

        <FilterRadios @filter="handleRadioFilter"/>

        <FilterDropdown :items="items" @filter="handCheckboxFilter"/>

    </div>
    <table class="w-full text-sm text-left text-gray-500">
        <thead class="test-xs text-gray-700 uppercase bg-gray-50">
            <tr>
                <th class="px-4 py-3">Id</th>
                <th class="px-4 py-3">assigned To</th>
                <th class="px-4 py-3">Status</th>
                <th class="px-4 py-3">Title </th>
                <th class="px-4 py-3">Due at</th>
                <th class="px-4 py-3">
                    <span class="sr-only">Actions</span>
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in filteredItens" :key="item.Id" class="border-b">
                <td class="px-4 py-3 font-medium text-gray-900">({item.id})</td>
                <td class="px-4 py-3 font-medium text-gray-900">({item.user.name})</td>
                <td class="px-4 py-3"({item.Status})></td>
                <td class="px-4 py-3"({item.Title})></td>
                <td class="px-4 py-3 flex items-centere justify-end">
                    <a href="" class="text-indigo-500 houver:underline">Details</a>
                </td>
            </tr>
        </tbody>
    </table>
 </div>
</template>