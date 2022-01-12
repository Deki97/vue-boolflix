<template>
        <div class="single-movie">
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
                Voto: {{ objectMovie.vote_average }}
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleMovie',
    props: {
        objectMovie: Object
    }

}
</script>


<style lang="scss" scoped>
.single-movie {
    margin: 30px 10px;

    .original-language {
        img {
            width: 20px;
        }
    }
}
</style>