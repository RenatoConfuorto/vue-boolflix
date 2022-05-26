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
      movieArray: [],
      seriesArray: [],
    }
  },
  methods: {
    searchElements(event){
      //bloccare la funzione se non c'è scritto nulla
      if(event.trim() === '')return;
      
      const params = {
        api_key: '8bf465eef8f09c9e78a545d8385e1644',
        include_adult: 'false',
        query: event.trim(),
      };

      const movieReq = axios.get('https://api.themoviedb.org/3/search/movie', {params});
      const seriesReq = axios.get('https://api.themoviedb.org/3/search/tv', {params});

      axios.all([movieReq, seriesReq])
      .then( (resp) => {
        console.log(resp);
        this.movieArray = resp[0].data.results;
        this.seriesArray = resp[1].data.results;
      });

      /*
      //cercare i film
      axios
      .get('https://api.themoviedb.org/3/search/movie', {params})
      .then((resp) => {
        // console.log(resp.data.results);
        this.movieArray = resp.data.results;
        // console.log(this.movieArray);
      });

      //cercare le serie tv
      
      axios
      .get('https://api.themoviedb.org/3/search/tv', {params})
      .then( (resp) => {
        // console.log(resp);
        this.seriesArray = resp;
      });
      */
    }
  },
  created() {
    document.title = 'Boolfix';
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";
@import "./style/variables.scss";
@import '~@fortawesome/fontawesome-free/css/all.min.css';

</style>
