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
    getDataFromMovieApi() {
      if (this.store.searchFilm.trim() != '') {
        axios
          .get('https://api.themoviedb.org/3/search/movie?api_key=28796c639fb17f6004d20cb8b0eea28d&language=it-IT&query=' + this.store.searchFilm)
          .then((resp) => {
            this.store.allFilms = resp.data.results;
            console.log(resp.data.results)

            this.allFilmsFlags();
          })
      }
      else {
        this.store.allFilms = [];
      }
    },
    getDataFromSeriesApi() {
      if (this.store.searchFilm.trim() != '') {
        axios
          .get('https://api.themoviedb.org/3/search/tv?api_key=28796c639fb17f6004d20cb8b0eea28d&language=it-IT&query=' + this.store.searchFilm)
          .then((resp) => {
            this.store.allSeries = resp.data.results;
            console.log(resp.data.results)

          })
      }
      else {
        this.store.allFilms = [];
      }
    },
    allFilmsFlags() {
      this.store.allFilms = this.store.allFilms.map(film => {
        return {
          ...film,
          original_language: `https://flagsapi.com/${film.original_language.toUpperCase()}/shiny/32.png`
        }
      })
    }
  },
  
}
</script>

<template>
  <div>
    <AppHeader @performSearch="getDataFromMovieApi(), getDataFromSeriesApi() "/>
    
    <AppMain />
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
@import "bootstrap/scss/bootstrap";
</style>
