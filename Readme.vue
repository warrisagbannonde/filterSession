<template>
    <form @submit.prevent>
        <input class="ml-3 mt-5 rounded shadow h-10 w-56" type="text" placeholder="Rechercher un nom..."
            v-model="searchValue">
        <button type="button" class=" ml-4 bg-amber-500 py-2 px-5 rounded-lg shadow-sm text-white hover:bg-amber-400"
            @click="filterUsers">Filtrer</button>
    </form>
    <table class="w-full whitespace-nowrap">
        <thead>
            <tr class="text-left font-bold">
                <th class="pb-4 pt-6 px-6 opacity-70">id</th>
                <th class="pb-4 pt-6 px-6 opacity-70">firstname</th>
                <th class="pb-4 pt-6 px-6 opacity-70">lastname</th>
                <th class="pb-4 pt-6 px-6 opacity-70">email</th>
                <th class="pb-4 pt-6 px-6 opacity-70">phone</th>
            </tr>
        </thead>
        <tbody>
            <tr class="p-4 hover:bg-gray-100 focus:within:bg-gray-100" v-for="(intern, index) in filteredUsers"
                :key="intern.id" :int="intern">
                <td class="border-t px-6 py-4 m-6">{{ index + 1 }}</td>
                <td class="border-t px-6 py-4 m-6">{{ intern.firstname }}</td>
                <td class="border-t px-6 py-4 m-6">{{ intern.lastname }}</td>
                <td class="border-t px-6 py-4 m-6">{{ intern.email }}</td>
                <td class="border-t px-6 py-4 m-6">{{ intern.phone }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script setup>
import { ref, watch } from 'vue';


const props = defineProps(['interns']);
const searchValue = ref('');

let filteredUsers = ref(props.interns);

function filterUsers() {
    filteredUsers.value = props.interns.filter((intern) =>
        intern.firstname.toLowerCase().includes(searchValue.value.toLowerCase()) ||
        intern.lastname.toLowerCase().includes(searchValue.value.toLowerCase())
    );
}

watch(searchValue, () => {
    filterUsers();
});
</script>

