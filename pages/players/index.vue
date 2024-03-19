// pages/players.vue

<template>
    <div class="players-page">
        <h1>Les joueurs</h1>
        <DataTable :value="players" paginator :rows="5" :rowsPerPageOptions="[5, 10, 20, 50]" tableStyle="min-width: 100%" class="table">
            <Column field="first_name" header="First Name"></Column>
            <Column field="last_name" header="Last Name"></Column>
            <Column header="Profile">
                <template #body="slotProps">
                    <nuxt-link :to="`/players/${slotProps.data.slug}`">View Profile</nuxt-link>
                </template>
            </Column>
        </DataTable>
    </div>
</template>




<script>

import Vue from 'vue';
import PrimeVue from 'primevue/config';
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';

Vue.use(PrimeVue);
Vue.component('DataTable', DataTable);
Vue.component('Column', Column);

export default {
    async asyncData({ $axios }) {
        try {
            const { data } = await $axios.get('/api/players');
            console.log('Données récupérées (joueurs):', data.data); 
            return { players: data.data };
        } catch (error) {
            console.error('Erreur lors de la récupération des joueurs:', error);
            return { players: [] };
        }
    }
}


</script>

<style>
.table {
    width: 100%;
}

</style>
