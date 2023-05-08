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
  
    // Metodo per cercare un film
    searchFilm() {
      axios
        .get("https://api.themoviedb.org/3/search/movie?api_key=eb01afe2b45b7303c28f1174082827ed",
          {
            params:
            {
              query: this.store.searchText, // Parola chiave per la ricerca del film
              language: 'it-IT'             // Lingua in cui restituire i risultati
            }
          }
        )
        .then((response) => {
          this.store.films = response.data.results  // Aggiorna l'elenco dei film con i risultati della ricerca
        });
    },

    searchSerie() {
      axios
        .get("https://api.themoviedb.org/3/search/tv?api_key=eb01afe2b45b7303c28f1174082827ed",
          {
            params:
            {
              query: this.store.searchText,
              language: 'it-IT'                       // Lingua in cui restituire i risultati
            }
          }
        )
        .then((response) => {
          this.store.series = response.data.results   // Aggiorna l'elenco delle serie TV con i risultati della ricerca
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
@use "./styles/main.scss";
</style>
