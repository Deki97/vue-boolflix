<template>
    <main>
        <div class="container">

            <!-- Lista di tutti i film restituiti -->
            <h2>Film</h2>
            <div class="movies">
                <SingleCard v-for="(movie, index) in moviesArray" :key="index" :objectCard="movie" />
            </div>

            <!-- Lista di tutte le serie TV restituite -->
            <h2>Serie TV</h2>
            <div class="series">
                <SingleCard v-for="(serie, index) in seriesArray" :key="index" :objectCard="serie" />
            </div>
        </div>
    </main>
</template>


<script>
import SingleCard from './SingleCard.vue';


export default {
    name: 'Main',
    components: {
        SingleCard
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