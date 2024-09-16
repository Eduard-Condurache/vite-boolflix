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
    singleFilmCard
  }
}
</script>

<template>
  <main>
    <div class="container">
      <div class="film-container row d-flex justify-content-center">
        <div v-for="(film, index) in store.allFilms" :key="index" class="col-2 m-2 bg-primary">
          <singleFilmCard :film="film"/>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>

</style>
