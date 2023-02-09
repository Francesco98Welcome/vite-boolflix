<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store
    }
  },
  methods: {
    searchFilm() {
      axios
        .get("https://api.themoviedb.org/3/search/movie?api_key=eb01afe2b45b7303c28f1174082827ed",
          {
            params:
              { query: store.searchText }
          }
        )
        .then((response) => {
          this.store.films = response.data.results
        });
      console.log('ciao');
    },

    searchSerie() {
      axios
        .get("https://api.themoviedb.org/3/search/tv?api_key=eb01afe2b45b7303c28f1174082827ed",
          {
            params:
              { query: store.searchText }
          }
        )
        .then((response) => {
          this.store.series = response.data.results
        });
    },
  }
}
</script>

<template>
  <AppHeader @performSearch="searchFilm(); searchSerie();" />
  <AppMain />

</template>

<style lang="scss">
@use "./styles/main.scss"
</style>
