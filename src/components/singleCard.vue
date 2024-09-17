<script>

export default {
  props: {
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    posterPath: String
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
      const imagePath = `https://image.tmdb.org/t/p/w342` + this.posterPath;

      return imagePath
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
  <div>
    <div class="poster-image">
      <img :src="posterImage" :alt="title">
    </div>
      
    <div class="infos">
      <div class="title">
        {{ checkTitle }}
      </div>

      <div v-if="title != originalTitle" class="original-title">
        {{ originalTitle }}
      </div>

      <div class="flag-icons">
        <img :src="getFlag(language)" :alt="title">
      </div>

      <div class="stars-review">
        <div class="d-inline-block" v-for="(star, index) in 5" :key="index">
          <font-awesome-icon 
            :icon="starRating(index)" />
        </div>
      </div>
    </div>
  </div>

</template>

<style lang="scss" scoped>
  .flag-icons img {
    width: 25px;
  }

  .poster-image img {
    max-width: 100%;
  }

</style>
