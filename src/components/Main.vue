<template>
    <main>
        <div class="container">

            <!-- Lista di tutti i film restituiti -->
            <h2>Film</h2>
            <div class="movies">
                <SingleMovie v-for="(movie, index) in moviesArray" :key="index" :objectMovie="movie" />
            </div>

            <!-- Lista di tutte le serie TV restituite -->
            <h2>Serie TV</h2>
            <div class="series">
                <SingleMovie v-for="(serie, index) in seriesArray" :key="index" :objectMovie="serie" />
            </div>
        </div>
    </main>
</template>


<script>
import SingleMovie from './SingleMovie.vue';


export default {
    name: 'Main',
    components: {
        SingleMovie
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
    padding: 50px 0;

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