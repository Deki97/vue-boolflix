<template>
    <main>
        <div class="container">

            <h2>Film</h2>
            <div class="movies">
                <SingleMovie v-for="(movie, index) in moviesArray" :key="index" :objectMovie="movie" />
            </div>

            <h2>Serie TV</h2>
            <div class="series">
                <SingleSerie v-for="(serie, index) in seriesArray" :key="index" :objectSerie="serie" />
            </div>
        </div>
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
    background-color: #383838;

    .container {

        .movies,
        .series {
            display: flex;
            overflow-x: auto;
        }

        h2 {
            margin-left: 10px;
            padding-top: 50px;
            font-size: 30px;
            text-transform: uppercase;
            color: white;
        }
    }
    
}
</style>