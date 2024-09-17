<script>
export default {
  props: {
    title: String,
    originalTitle: String,
    language: String,
    vote: Number
  },
  methods: {
    getFlag(lang) {
      const validLangs = {
        en: 'en.gif',
        it: 'it.gif',
        ja: 'ja.gif'
      }

      if (lang in validLangs) {
        return '/src/assets/langIcons/' + validLangs[lang];
      }
      else {
        return '/src/assets/langIcons/worldflag.png'
      }
   }
  }
}
</script>

<template>
  <div>
    <div>
      {{ title }}
    </div>

    <div>
      {{ originalTitle }}
    </div>

    <div>
      <img :src="getFlag(language)" :alt="title">
    </div>

    <div>
      {{ vote }}
    </div>
  </div>

</template>

<style lang="scss" scoped>
  img {
    width: 25px;
  }
</style>
