<template>
  <div id="app">
    <Header @filterMovies="filterApi" />

    <Main v-for="(item, index) in filterApi" :key="index" :objectCard="item" />

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
      queryText: '',
      arrayFiltered: []
    }
  },
  methods: {
    filterApi: function() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'e60cf25f0e89f321c0a6aab650e9fb5e',
          query: this.queryText
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
