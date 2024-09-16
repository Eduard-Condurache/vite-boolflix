<script>
import { store } from '../store.js'
import singleFilmCard from './singleFilmCard.vue';
import singleSeriesCard from './singleSeriesCard.vue'
export default {
  data() {
    return { 
      store
    }
  },
  components: {
    singleFilmCard,
    singleSeriesCard
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
          <singleFilmCard :film="film"/>
        </div>

        <div>
          <h1 class="text-center">TV SERIES</h1>
        </div>
        <div v-for="(series, index) in store.allSeries" :key="index" class="col-2 m-2 bg-secondary">
          <singleSeriesCard :series="series"/>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>

</style>
