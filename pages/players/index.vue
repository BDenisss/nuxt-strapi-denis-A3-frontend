// pages/players.vue

<template>
    <div class="players-page">
        <h1>Les joueurs</h1>
        <ul>
            <li v-for="player in players" :key="player.id">
                <nuxt-link :to="`/players/${player.slug}`">
                    {{ player?.first_name }} {{ player?.last_name }}
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>




<script>




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

</style>
