<template>
  <div id="app">
    <AppHeader @search="searchElements($event)"/>

    <main>
      <AppListDisplay :elementArray="movieArray"/>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import AppListDisplay from "./components/AppListDisplay.vue";

export default {

  name: 'App',
  components: {
    AppHeader,
    AppListDisplay,
  },
  data(){
    return{
      searchKey: '',
      movieArray: [],
    }
  },
  methods: {
    searchElements(event){
      //bloccare la funzione se non c'è scritto nulla
      if(event.trim() === '')return;
      this.searchKey = event;
      const params = {
        api_key: '8bf465eef8f09c9e78a545d8385e1644',
        language: 'it-IT',
        page: '4',
        include_adult: 'false',
        query: event.trim(),
      };
      // console.log(params);
      axios
      .get('https://api.themoviedb.org/3/search/movie', {params})
      .then((resp) => {
        console.log(resp.data.results);
        this.movieArray = resp.data.results;
        console.log(this.movieArray);
      });
    }
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";
@import "./style/variables.scss";

</style>
