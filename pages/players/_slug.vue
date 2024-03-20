
<template>
    <div v-if="player" class="player-page">
        <div class="player-profile">
            <div v-if="player.image" class="player-image">
                <img :src="player.image.url" :alt="`Image de ${player.first_name} ${player.last_name}`">
            </div>
            <div class="player-details">
                <h1 class="player-name">{{ player.first_name }} {{ player.last_name }}</h1>
                <div class="info-section">
                    <h2 class="player-ranking">World Ranking <span>#{{ player.ranking }}</span></h2>
                    <div class="player-info">
                        <div class="player-country"><img :src="player.country_player.url" :alt="`Flag of ${player.country}`">{{ player.country }}</div>
                        <div class="player-age">Age: {{ player.age }}</div>
                        <div class="player-style">Style: {{ player.style }}</div>
                    </div>
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

.player-page {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
}

.player-profile {
    display: flex;
    background-color: black;
    color: white;
    padding: 20px;
    border-radius: 10px;
}

.player-image img {
    width: 300px;
    height: auto;
    border-radius: 20px;
    margin-right: 20px;
}

.player-details {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.player-name {
    margin-bottom: 10px;
    font-size: 2rem;
    text-align: start;
}

.info-section {
    display: flex;
    align-items: center;
    gap: 20px;
}

.player-ranking {
    font-size: 1.5rem;
    margin-right: 20px;
}

.player-info {
    display: flex;
    flex-direction: column;
}

.player-country, .player-age, .player-style {
    margin: 5px 0;
}

.player-country img {
    width: 24px;
    height: auto;
    margin-right: 5px;
}


</style>
