<template>
  <div id="app">
    <AppHeader @search="searchElements($event)"/>

    <main>
      <h2>Film</h2>
      <AppListDisplay :elementArray="movieArray"/>
      <h2>Serie Tv</h2>
      <AppListDisplay :elementArray="seriesArray"/>
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
      seriesArray: [],
    }
  },
  methods: {
    searchElements(event){
      //bloccare la funzione se non c'è scritto nulla
      if(event.trim() === '')return;
      this.searchKey = event;
      const params = {
        api_key: '8bf465eef8f09c9e78a545d8385e1644',
        include_adult: 'false',
        query: event.trim(),
      };
      // console.log(params);
      //cercare i film
      axios
      .get('https://api.themoviedb.org/3/search/movie', {params})
      .then((resp) => {
        // console.log(resp.data.results);
        this.movieArray = resp.data.results;
        // console.log(this.movieArray);
      });

      //cercare le serie tv
      /*
      axios
      .get('https://api.themoviedb.org/3/search/tv', {params})
      .then( (resp) => {
        // console.log(resp);
        this.seriesArray = resp;
      });
      */
    }
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";
@import "./style/variables.scss";

</style>
