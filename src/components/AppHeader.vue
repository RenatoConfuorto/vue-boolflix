<template>
  <header>
    <div class="logo">
      <h1>Boolfix</h1>
    </div>
    <div class="nav-bar">
      <NavBarList/>
    </div>
    <div class="search-bar">
      <input type="text" placeholder="Cerca" v-model="searchText">
      <button @click="$emit('search', searchText)">Cerca</button>
    </div>
  </header>

</template>

<script>
import NavBarList from "./NavBarList.vue";

export default {
  name: 'AppHeader',
  components: {
    NavBarList,
  },
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
  padding: 0 10px;
  width: 100%;
  height: $app-header-height;
  background-color: black;
  display: flex;
  align-items: center;

  .logo{
    color: $brand-primary-color;
    text-transform: uppercase;
    font-size: 1.3rem;
  }

  .search-bar{
    margin-left: auto;
    border: 1px solid $brand-primary-color;

    input{
      padding: 2px;
      height: 1.5rem;
      border: 0;

      &:focus-visible{
        outline: 0;
      }
    }

    button{
      padding: 5px 10px;
      height: 1.5rem;
      border: 0;
      background-color: $brand-primary-color;
    }
  }

  
}
</style>