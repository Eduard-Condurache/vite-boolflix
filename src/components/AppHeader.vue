<script>
import axios from 'axios'
import { store } from '../store.js'

export default {
  data() {
    return { 
      store
    }
  },
  methods: {
    performSearch() {
      this.$emit('performSearch');
    }
  }
}
</script>

<template>
  <header>
    <div class="container">
      <div class="row">
        <div class="col-12 d-flex justify-content-between align-items-center">
          <div>
            <div class="logo">
              <h1>
                Boolflix
              </h1>
            </div>
          </div>

          <div>
            <form 
              class="d-flex"
              @submit.prevent="performSearch()">
              <input 
                type="text" 
                class="form-control"
                v-model="store.searchFilm"
                placeholder="Cerca un film">

                <button 
                  class="btn btn-primary ms-3" 
                  type="submit">
                  Search
                </button>
            </form>
          </div>     
        </div>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
  h1 {
    text-align: center;
  }
</style>
