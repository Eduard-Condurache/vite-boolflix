<script>
import { store } from '../store.js'
import singleFilmCard from './singleFilmCard.vue';
export default {
  data() {
    return { 
      store
    }
  },
  components: {
    singleFilmCard,
  }
}
</script>

<template>
  <main>
    <div class="container">
      <div class="movies-container row d-flex justify-content-center">
        <div>
          <h1 class="text-center">FILMS</h1>
        </div>
        <div v-for="(film, index) in store.allFilms" :key="index" class="col-2 m-2 bg-primary">
          <singleFilmCard 
            :title="film.title"
            :originalTitle="film.original_title"
            :language="film.original_language"
            :vote="film.vote_average"/>
        </div>

        <div>
          <h1 class="text-center">TV SERIES</h1>
        </div>
        <div v-for="(series, index) in store.allSeries" :key="index" class="col-2 m-2 bg-secondary">
          <singleFilmCard 
            :title="series.name"
            :originalTitle="series.original_name"
            :language="series.original_language"
            :vote="series.vote_average"/>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>

</style>
