<template>
        <div class="single-movie">
            <div class="card-poster">
                <div class="poster">
                    <img :src="this.defaultPath + objectMovie.poster_path"  :alt="objectMovie.name">
                </div>
            </div>

            <div class="card-info">
                <div class="title">
                    Titolo: {{ objectMovie.title }}
                </div>

                <div class="original-title">
                    Titolo Originale: {{ objectMovie.original_title }}
                </div>

                <div class="original-language">
                    <!-- {{ objectMovie.original_language }} -->
                    Lingua: 
                    <span v-if="(objectMovie.original_language === 'en') || (objectMovie.original_language === 'it') || (objectMovie.original_language === 'fr')">
                        <img :src="require('../assets/img/' +  objectMovie.original_language + '.png')" :alt="objectMovie.original_language">
                    </span>

                    <span v-else>
                        {{ objectMovie.original_language }}
                    </span>
                </div>

                <div class="vote-average">
                    Voto: 
                    <span>
                        {{ voteCeiled }}
                    </span>
                </div>

                <div class="overview">
                    Overview: {{ objectMovie.overview }}
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
    }

    .card-info {
        display: none;
        height: 100%;
        width: 100%;
        color: white;
        background-color: black;
        padding: 20px 10px;
        overflow: hidden;

        .original-language {
            img {
                width: 20px;
            }
        }
    }
    
    &:hover .card-poster{
        display: none;
    }

    &:hover .card-info {
        display: block;
    }
}
</style>