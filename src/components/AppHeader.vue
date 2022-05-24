<template>
  <header>
    <label for="search">Testo ricerca</label>
    <input type="text" v-model="searchText">
    <button @click="$emit('search', searchText)">Cerca</button>
  </header>

</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return{
      searchText: '',
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

header{
  width: 100%;
  height: $app-header-height;
  background-color: grey;
}
</style>