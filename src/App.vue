<template>
  <div id="app">
    <Header @filterApi="searchApi" />

    <Main :moviesArray="moviesArrayFiltered" :seriesArray="seriesArrayFiltered"/>

  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data: function() {
    return {
      moviesArrayFiltered: [],
      seriesArrayFiltered: [],
      queryText: '',
      api_key: 'e60cf25f0e89f321c0a6aab650e9fb5e'
    };
  },
  methods: {
    searchApi: function(userText) {
      this.queryText = userText;
      this.searchMovies();
      this.searchSeries();
    },
    searchMovies: function() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.api_key,
          query: this.queryText,
          language: 'it-IT'
        }
      })
      .then((response) => {
        this.moviesArrayFiltered = response.data.results;
      });
    },
    searchSeries: function() {
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.api_key,
          query: this.queryText,
          language: 'it-IT'
        }
      })
      .then((response) => {
        this.seriesArrayFiltered = response.data.results;
      })
    }
  }
};
</script>

<style>

</style>
