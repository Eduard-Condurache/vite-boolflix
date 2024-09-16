<script>
export default {
  props: {
    series: Object
  },
}
</script>

<template>
  <div>
    <div>
      {{ series.name }}
    </div>

    <div>
      {{ series.original_name }}
    </div>

    <div>
      <img :src="series.original_language">
    </div>

    <div>
      {{ series.vote_average }}
    </div>
  </div>
</template>

<style lang="scss" scoped>

</style>
