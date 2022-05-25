<template>
  <div class="card">
    <!-- <img :src="`http://image.tmdb.org/t/p//w500/${elementObj.poster_path}`" alt=""> -->
    <h2>{{ elementObj.title }}</h2>
    <h3>{{ elementObj.original_title }}</h3>
    <div class="flag-container">
      <img v-if="hasFlag" :src="require(`../assets/img/${elementObj.original_language}.svg`)" alt="" class="flag">
      <p v-else>{{ elementObj.original_language }}</p>
    </div>
    <p>{{ elementObj.vote_average }}</p>

    <!-- titolo
    titolo originale
    lingua
    voto -->
  </div>
</template>

<script>
/*
import imageDe from "../assets/img/de.svg";
import imageIt from "../assets/img/it.svg";
import imageEs from "../assets/img/es.svg";
import imageFr from "../assets/img/fr.svg";
import imageGb from "../assets/img/gb.svg";
*/

export default {
  name: 'ElementCard',
  props: {
    elementObj: Object,
  },
  data(){
    return{
      lingua: 'it',
      flags: ['de', 'en', 'es', 'fr', 'it'],
      /*
      imageIt: imageIt,
      imageDe: imageDe,
      imageEs: imageEs,
      imageFr: imageFr,
      imageGb: imageGb,
      */
    }
  },
  computed: {
    hasFlag(){
      return this.flags.includes(this.elementObj.original_language);
    }
  },
  methods: {
    /*
    getLanguages(){
      this.flagHtml = `<img src="${imageIt}" alt="italia" class="flag">`;
      if(this.movieObj.original_language === 'en')this.flagHtml += `<img src="${imageGb}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'de')this.flagHtml += `<img src="${imageDe}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'es')this.flagHtml += `<img src="${imageEs}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'fr')this.flagHtml += `<img src="${imageFr}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language !== 'it')this.flagHtml += ` - ${this.movieObj.original_language}`;
    }
    */
  },
  created(){
    // this.getLanguages();
  }
  
}
</script>

<style lang="scss" scoped>
.card{
  min-height: 150px;
  border: 1px solid black;
  padding: 5px;
  margin: 5px;
  margin-bottom: 10px;
  width: calc(25% - 10px);
  background-color: white;
  display: flex;
  flex-direction: column;

  .flag-container{
    
    .flag{
      width: 20px;
    }

  }

}

</style>