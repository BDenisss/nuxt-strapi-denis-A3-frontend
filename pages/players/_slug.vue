
<template>
    <div v-if="player" class="player-page">

        <div class="player-container">
                <div v-if="player.image" class="player-image">
                    <img :src="player.image.url" :alt="`Image de ${player.first_name} ${player.last_name}`">
                </div>

            <div class="player-details">
                <div>
                    <h1>{{ player.first_name }} {{ player.last_name }}</h1>
                </div>
                <div>
                    <p><strong>Âge :</strong> {{ player.age }}</p>
                    <p><strong>Pays :</strong> {{ player.country }}</p>
                    <p><strong>Classement :</strong> {{ player.ranking }}</p>
                    <p><strong>Style :</strong> {{ player.style }}</p>
                </div>
            </div>
        </div>
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
            return { player: null };
        }
    }
}
</script>

<style scoped>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

h1 {
    text-align: center;
}

.player-container {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
}
.player-details {
    display: flex;
    flex-direction: column;

    gap: 16px;
}

.player-image img {
    width: 200px; 
    height: auto;
    border-radius: 10px; 
}

.player-details {
    margin-top: 20px;
}

.player-details p {
    margin: 5px 0; 
}
</style>
