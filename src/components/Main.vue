<template>
    <main>
        <h2>Film</h2>
        <SingleMovie v-for="(movie, index) in moviesArray" :key="index" :objectMovie="movie" />

        <h2>Serie TV</h2>
        <SingleSerie v-for="(serie, index) in seriesArray" :key="index" :objectSerie="serie" />

    </main>
</template>


<script>
import SingleMovie from './SingleMovie.vue';
import SingleSerie from './SingleSerie.vue';


export default {
    name: 'Main',
    components: {
        SingleMovie,
        SingleSerie
    },
    props: {
        moviesArray: Array,
        seriesArray: Array
    }
}
</script>


<style lang="scss" scoped>
main {
    h2 {
        margin-left: 10px;
    }
}
</style>