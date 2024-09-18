<script>
import { store } from '../store.js'
import singleCard from './singleCard.vue';
export default {
  data() {
    return { 
      store
    }
  },
  components: {
    singleCard,
  }
}
</script>

<template>
  <main>
    <div>
      <div class="px-5">

        <!-- TOP RATED SECTION -->
        <div class="toprated-container row my-4">
          <div v-for="(top, index) in store.topRated" 
            :key="index" 
            class="single-movie col-6 col-sm-4 col-lg-3 col-xl-2">
          <singleCard 
            :title="top.title"
            :originalTitle="top.original_title"
            :language="top.original_language"
            :vote="top.vote_average"
            :posterPath="top.poster_path"
            :overview="top.overview"/>
          </div>
        </div>

        <!-- MOVIE SECTION -->
        <div class="my-4">
          <h1 class="text-start text-white">Film</h1>
        </div>
        <div class="movie-container row">
          <div v-for="(film, index) in store.allFilms" 
            :key="index" 
            class="single-movie col-6 col-sm-4 col-lg-3 col-xl-2">
          <singleCard 
            :title="film.title"
            :originalTitle="film.original_title"
            :language="film.original_language"
            :vote="film.vote_average"
            :posterPath="film.poster_path"
            :overview="film.overview"/>
          </div>
        </div>

        <!-- SERIES SECTION -->
        <div class="my-4">
          <h1 class="text-start text-white">Tv series</h1>
        </div>
        <div class="series-container row">
          <div 
            v-for="(series, index) in store.allSeries" 
            :key="index" 
            class="single-series col-6 col-sm-4 col-lg-3 col-xl-2">

          <singleCard 
            :title="series.name"
            :originalTitle="series.original_name"
            :language="series.original_language"
            :vote="series.vote_average"
            :posterPath="series.poster_path"
            :overview="series.overview"/>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>

.single-movie,
.single-series {
  margin-bottom: 20px;
}

</style>
