<template>
        <div class="single-movie">
            <!-- Immagine di copertina -->
            <div class="card-poster">
                <div v-if="objectMovie.poster_path" class="poster">
                    <img :src="this.defaultPath + objectMovie.poster_path"  :alt="objectMovie.name">
                </div>
                <!-- Se l'API non ha l'immagine di copertina, faccio apparire un testo sostitutivo -->
                <div v-else class="no-image">
                    Nessuna immagine disponibile
                </div>
            </div>

            <!-- Informazioni sul singolo film / serie TV -->
            <div class="card-info">
                <!-- Titolo -->
                <div v-if="objectMovie.title" class="title">
                    <span class="bold">
                        Titolo:
                    </span> 
                    {{ objectMovie.title }}
                </div>
                <div v-else>
                    <span class="bold">
                        Titolo:
                    </span> 
                    {{ objectMovie.name }}
                </div>

                <!-- Titolo Originale -->
                <div v-if="objectMovie.original_title" class="original-title">
                    <span class="bold">
                        Titolo Originale:
                    </span>
                    {{ objectMovie.original_title }}
                </div>
                <div v-else>
                    <span class="bold">
                        Titolo Originale:
                    </span>
                    {{ objectMovie.original_name }}
                </div>

                <!-- Lingua Originale -->
                <div class="original-language">
                    <!-- {{ objectMovie.original_language }} -->
                    <span class="bold">
                        Lingua:
                    </span> 
                    <span v-if="(objectMovie.original_language === 'en') || (objectMovie.original_language === 'it') || (objectMovie.original_language === 'fr')">
                        <img :src="require('../assets/img/' +  objectMovie.original_language + '.png')" :alt="objectMovie.original_language">
                    </span>

                    <span v-else>
                        {{ objectMovie.original_language }}
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
                <div v-if="objectMovie.overview" class="overview">
                    <span class="bold">
                        Overview:
                    </span>
                    {{ objectMovie.overview }}
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
    name: 'SingleMovie',
    data: function() {
        return {
            defaultPath: 'https://image.tmdb.org/t/p/w342',
            voteCeiled: Math.ceil(this.objectMovie.vote_average / 2)
        }
    },
    props: {
        objectMovie: Object
    }
}
</script>


<style lang="scss" scoped>
.single-movie {
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
    
    // Effetto hover single-movie
    &:hover .card-poster {
        display: none;
    }

    &:hover .card-info {
        display: block;
    }


}
</style>