<template>
        <div class="single-card">
            <!-- Immagine di copertina -->
            <div class="card-poster">
                <div v-if="objectCard.poster_path" class="poster">
                    <img :src="this.defaultPath + objectCard.poster_path"  :alt="objectCard.name">
                </div>
                <!-- Se l'API non ha l'immagine di copertina, faccio apparire un testo sostitutivo -->
                <div v-else class="no-image">
                    Nessuna immagine disponibile
                </div>
            </div>

            <!-- Informazioni sul singolo film / serie TV -->
            <div class="card-info">
                <!-- Titolo -->
                <div v-if="objectCard.title" class="title">
                    <span class="bold">
                        Titolo:
                    </span> 
                    {{ objectCard.title }}
                </div>
                <div v-else>
                    <span class="bold">
                        Titolo:
                    </span> 
                    {{ objectCard.name }}
                </div>

                <!-- Titolo Originale -->
                <div v-if="objectCard.original_title" class="original-title">
                    <span class="bold">
                        Titolo Originale:
                    </span>
                    {{ objectCard.original_title }}
                </div>
                <div v-else>
                    <span class="bold">
                        Titolo Originale:
                    </span>
                    {{ objectCard.original_name }}
                </div>

                <!-- Lingua Originale -->
                <div class="original-language">
                    <!-- {{ objectCard.original_language }} -->
                    <span class="bold">
                        Lingua:
                    </span> 
                    <span v-if="(objectCard.original_language === 'en') || (objectCard.original_language === 'it') || (objectCard.original_language === 'fr')">
                        <img :src="require('../assets/img/' +  objectCard.original_language + '.png')" :alt="objectCard.original_language">
                    </span>

                    <span v-else>
                        {{ objectCard.original_language }}
                    </span>
                </div>

                <!-- Valutazione media -->
                <div class="vote-average">
                    <span class="bold">
                        Voto: 
                    </span>
                    <!-- Conversione della valutazione in stelline -->
                    <span v-for="(n, index) in 5" :key="index">
                        <span v-if="n <= voteCeiled">
                            <i class="fas fa-star"></i>
                        </span>
                        <span v-else>
                            <i class="far fa-star"></i>
                        </span>
                    </span>
                </div>

                <!-- Trama -->
                <div v-if="objectCard.overview" class="overview">
                    <span class="bold">
                        Overview:
                    </span>
                    {{ objectCard.overview }}
                </div>
                <!-- Se l'API non ha la descrizione, faccio apparire un testo sostitutivo -->
                <div v-else>
                    Nessuna descrizione disponibile
                </div>
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleCard',
    data: function() {
        return {
            defaultPath: 'https://image.tmdb.org/t/p/w342',
            voteCeiled: Math.ceil(this.objectCard.vote_average / 2)
        }
    },
    props: {
        objectCard: Object
    }
}
</script>


<style lang="scss" scoped>
.single-card {
    margin: 30px 10px;
    border: 2px solid white;
    height: 507px;
    width: 342px;
    cursor: pointer;
    flex-shrink: 0;

    .card-poster {
        height: 100%;
        width: 100%;
        overflow: hidden;

        .no-image {
            position: relative;
            text-align: center;
            top: 50%;
            color: white;
        }
    }

    .card-info {
        display: none;
        height: 100%;
        width: 100%;
        color: white;
        background-color: black;
        padding: 20px 10px;
        overflow-y: auto;

        .original-language {
            img {
                width: 20px;
            }
        }
    }
    
    // Effetto hover single-card
    &:hover .card-poster {
        display: none;
    }

    &:hover .card-info {
        display: block;
    }


}
</style>