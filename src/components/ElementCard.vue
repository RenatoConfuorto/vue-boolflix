<template>
  <div class="card">
    <img :src="`http://image.tmdb.org/t/p//w500/${movieObj.poster_path}`" alt="">
    <h2>{{ movieObj.title }}</h2>
    <h3>{{ movieObj.original_title }}</h3>
    <div class="flag-container" v-html="flagHtml">
    </div>
    <p>{{ movieObj.vote_average }}</p>

    <!-- titolo
    titolo originale
    lingua
    voto -->
  </div>
</template>

<script>
import imageDe from "../assets/img/de.svg";
import imageIt from "../assets/img/it.svg";
import imageEs from "../assets/img/es.svg";
import imageFr from "../assets/img/fr.svg";
import imageGb from "../assets/img/gb.svg";


export default {
  name: 'ElementCard',
  props: {
    movieObj: Object,
  },
  data(){
    return{
      lingua: 'it',
      flagHtml: '',
      imageIt: imageIt,
      imageDe: imageDe,
      imageEs: imageEs,
      imageFr: imageFr,
      imageGb: imageGb,
    }
  },
  methods: {
    getLanguages(){

      this.flagHtml = `<img src="${imageIt}" alt="italia" class="flag">`;
      if(this.movieObj.original_language === 'en')this.flagHtml += `<img src="${imageGb}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'de')this.flagHtml += `<img src="${imageDe}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'es')this.flagHtml += `<img src="${imageEs}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language === 'fr')this.flagHtml += `<img src="${imageFr}" alt="italia" class="flag">`;
      else if(this.movieObj.original_language !== 'it')this.flagHtml += ` - ${this.movieObj.original_language}`;
      
    }
  },
  created(){
    this.getLanguages();
  }
  
}
</script>

<style lang="scss" scoped>
.card{
  margin-bottom: 10px;
  width: 25%;
  background-color: white;
  display: flex;
  flex-direction: column;

  .flag-container{
    display: inline-block;
    
    &>*{
      width: 20px;
      height: auto;
    }

  }

}

</style>