<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios'
import { store } from './store.js'

export default {
  data () {
    return {
      apiKey: '28796c639fb17f6004d20cb8b0eea28d',
      store,
      activeSearch: false
    }
  },
  created() {
    this.getDataFromTopRatedApi();
  },
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    getDataFromApi() {
      if (this.store.search.trim() != '') {
        const movieApiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=' + this.apiKey + '&language=it-IT&query=' + this.store.search;
        const seriesApiUrl = 'https://api.themoviedb.org/3/search/tv?api_key=' + this.apiKey + '&language=it-IT&query=' + this.store.search;

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

          this.activeSearch = true;
      } 
      else {
        this.store.allFilms = [];
        this.store.allSeries = [];
        this.activeSearch = true;
      }
    },
    getDataFromTopRatedApi() {
      axios
        .get('https://api.themoviedb.org/3/movie/top_rated?api_key=' + this.apiKey + '&language=it-IT')
        .then((resp) => {
          this.store.topRated = resp.data.results
          console.log(resp.data.results)
        })
    },
  }
  
}
</script>

<template>
  <div>
    <AppHeader @performSearch="getDataFromApi() "/>
    
    <AppMain :activeSearch="activeSearch"/>


  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import "bootstrap/scss/bootstrap";

</style>
