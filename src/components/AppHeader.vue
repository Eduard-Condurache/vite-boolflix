<script>
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
    <div class="px-5 py-3">
      <div class="row">
        <div class="col-12 d-flex justify-content-between align-items-center">
          <div>
            <div class="logo">
              <img src="/src/assets/img/Boolflix-18-09-2024.png" alt="logo">
            </div>
          </div>

          <div>
            <form 
              class="d-flex"
              @submit.prevent="performSearch()">
              <input 
                type="text" 
                class="header-input"
                v-model="store.search"
                placeholder="Cerca un film e una serie">

                <button 
                  class="btn btn-outline-light ms-3" 
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

  header {
    background-color: #0C0C0C;

    .header-input {
      border: 1px solid white;
      background-color: black;
      color: white;
      width: 200px;
      font-size: 0.9rem;
    }
  }
  .logo {
    width: 100px;
    margin-right: 10px;

    img {
      max-width: 100%;
    }
  }
</style>
