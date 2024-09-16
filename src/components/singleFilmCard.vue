<script>
export default {
  props: {
    film: Object
  }
}
</script>

<template>
  <div>
    <div>
      {{ film.title }}
    </div>

    <div>
      {{ film.original_title }}
    </div>

    <div>
      {{ film.original_language }}
    </div>

    <div>
      {{ film.vote_average }}
    </div>
  </div>
</template>

<style lang="scss" scoped>

</style>
