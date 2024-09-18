<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios'
import { store } from './store.js'

export default {
  data () {
    return {
      store
    }
  },
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    getDataFromApi() {
      if (this.store.searchFilm.trim() != '') {
        const movieApiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=28796c639fb17f6004d20cb8b0eea28d&language=it-IT&query=' + this.store.searchFilm;
        const seriesApiUrl = 'https://api.themoviedb.org/3/search/tv?api_key=28796c639fb17f6004d20cb8b0eea28d&language=it-IT&query=' + this.store.searchFilm;

        axios
          .get(movieApiUrl)
          .then((movieResp) => {
            this.store.allFilms = movieResp.data.results;
            console.log(movieResp.data.results);
          });

        axios
          .get(seriesApiUrl)
          .then((seriesResp) => {
            this.store.allSeries = seriesResp.data.results;
            console.log(seriesResp.data.results);
          });
      } 
      else {
        this.store.allFilms = [];
        this.store.allSeries = [];
      }
    }
  }
  
}
</script>

<template>
  <div class="page-container">
    <AppHeader @performSearch="getDataFromApi() "/>
    
    <AppMain />


  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import "bootstrap/scss/bootstrap";

.page-container {
  background-color: #141414;
}
</style>
