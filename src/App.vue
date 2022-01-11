<template>
  <div id="app">
    <Header @filterMovies="filterApi" />

    <SingleCard v-for="(item, index) in arrayFiltered" :key="index" :objectCard="item" />

  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import SingleCard from './components/SingleCard.vue';

export default {
  name: "App",
  components: {
    Header,
    SingleCard
  },
  data: function() {
    return {
      arrayFiltered: []
    }
  },
  methods: {
    filterApi: function(query) {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'e60cf25f0e89f321c0a6aab650e9fb5e',
          query,
          language: 'it-IT'
        }
      })
      .then((response) => {
        this.arrayFiltered = response.data.results;
      });
    }
  }
};
</script>

<style>

</style>
