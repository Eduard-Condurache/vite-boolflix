<script>

export default {
  props: {
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    posterPath: String,
    overview: String
  },
  methods: {
    getFlag(lang) {
      const validLangs = {
        en: 'en.gif',
        it: 'it.gif',
        ja: 'ja.gif',
        es: 'sp.gif',
        fr: 'fr.gif',
        cn: 'cn.gif'
      }

      if (lang in validLangs) {
        return '/src/assets/langIcons/' + validLangs[lang];
      }
      else {
        return '/src/assets/langIcons/worldflag.png'
      }
   },
   starRating (i) {
    if (this.ratingNumber > i) {
      return 'fa-solid fa-star';
    }
    else {
      return 'fa-regular fa-star';
    }
   }
   
  },
  computed: {
    posterImage () {
      if (this.posterPath != null) {
        const imagePath = `https://image.tmdb.org/t/p/w342` + this.posterPath;

        return imagePath 
      }
      else {
        return 'https://placehold.co/284x435/EEE/31343C?font=playfair-display&text=Weila!'
      }
      
    },
    ratingNumber() {
      return Math.round(this.vote / 2);
    },
    checkTitle() {
      if (this.title === this.originalTitle) {
        return this.originalTitle
      } else {
        return this.title;
      }
    },
  }
}
</script>

<template>
  <div class="poster-card">
    <img :src="posterImage" :alt="title">
      
    <div class="infos">
      <div class="title">
        Titolo:
        {{ checkTitle }}
      </div>

      <div v-if="title != originalTitle" class="original-title">
        Titolo originale:
        {{ originalTitle }}
      </div>

      <div class="flag-icons">
        Lingua:
        <img :src="getFlag(language)" :alt="title">
      </div>

      <div class="stars-review">
        Voto:
        <div class="d-inline-block" v-for="(star, index) in 5" :key="index">
          <font-awesome-icon 
            :icon="starRating(index)" />
        </div>
      </div>

      <div class="overview">
          Overview:
          {{ overview }}
      </div>
    </div>
  </div>

</template>

<style lang="scss" scoped>

@use '../assets/scss/partials/mixins.scss' as *;
@use '../assets/scss/partials/variables' as *;

.poster-card {
  @include maxSize;
  position: relative;
  transition: transform 0.3s ease, box-shadow 0.3s ease;

  > img {
    @include maxSize;
    display: block;
  }

  &:hover {
    transform: scale(1.2);
    z-index: 10;
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
  }

  .flag-icons img {
    width: 15px;
    height: 10px;
  }


  .infos {
    @include maxSize;
    top: 0;
    left: 0;
    position: absolute;
    background: rgba(0,0,0, 0.8);
    opacity: 0;
    transition: all 0.7s ease-in-out;
    color: white;
    cursor: pointer;
    padding: 20px 5px 20px 20px;
    display: flex;
    flex-direction: column;
    font-size: 0.9rem;

    .overview {
      flex-grow: 1;
      min-height: 100px;
      overflow-y: scroll;
      margin-top: 10px;
      font-size: 0.85rem;

      &::-webkit-scrollbar {
        display: none;
      }
      scrollbar-width: none;
    }
  }

  .infos:hover {
    opacity: 1;
  }
}
</style>
