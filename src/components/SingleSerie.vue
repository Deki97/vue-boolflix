<template>
        <div class="single-serie">
            <div class="title">
                Titolo: {{ objectSerie.name }}
            </div>

            <div class="original-title">
                Titolo Originale: {{ objectSerie.original_name }}
            </div>

            <div class="original-language">
                <!-- {{ objectSerie.original_language }} -->
                Lingua: 
                <span v-if="(objectSerie.original_language === 'en') || (objectSerie.original_language === 'it') || (objectSerie.original_language === 'fr')">
                    <img :src="require('../assets/img/' +  objectSerie.original_language + '.png')" :alt="objectSerie.original_language">
                </span>

                <span v-else>
                    {{ objectSerie.original_language }}
                </span>
            </div>

            <div class="vote-average">
                Voto: {{ objectSerie.vote_average }}
            </div>
        </div>
</template>


<script>

export default {
    name: 'SingleSerie',
    props: {
        objectSerie: Object
    }

}
</script>


<style lang="scss" scoped>
.single-serie {
    margin: 30px 10px;

    .original-language {
        img {
            width: 20px;
        }
    }
}
</style>