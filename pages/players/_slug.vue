
<template>
    <div v-if="player" class="player-page">
        <h1>{{ player.first_name }} {{ player.last_name }}</h1>

        <img v-if="player.image" :src="player.image.url" :alt="`Image de ${player.first_name} ${player.last_name}`">
    </div>
</template>

<script>

export default {
    async asyncData({ params, $axios }) {
        try {
            const { data } = await $axios.get(`/api/players?filters[slug][$eq]=${params.slug}&populate=*`);
            console.log('Joueur récupéré:', data.data[0]);
            return { player: data.data[0] }; 
        } catch (error) {
            console.error('Erreur lors de la récupération des détails du joueur:', error);
            // Ceci empêchera l'erreur si la page est chargée avec des données manquantes
            return { player: null };
        }
    }
}



</script>

<style scoped>

</style>s