<template>
  <div class="card">
    <img :src="`http://image.tmdb.org/t/p//w500/${movieObj.poster_path}`" alt="">
    <h2>{{ movieObj.title }}</h2>
    <h3>{{ movieObj.original_title }}</h3>
    <p>it - {{movieObj.original_language}}</p>
    <p>{{ movieObj.vote_average }}</p>

    <!-- titolo
    titolo originale
    lingua
    voto -->
  </div>
</template>

<script>
export default {
  name: 'ElementCard',
  props: {
    movieObj: Object,
  }
}
</script>

<style lang="scss" scoped>
.card{
  margin-bottom: 10px;
  width: 25%;
  background-color: white;
}

img{
  width: 100%;
  height: auto;
}
</style>