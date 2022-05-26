<template>
  <li class="card">
    <div class="card-content">
      <img :src="`http://image.tmdb.org/t/p//w500/${elementObj.poster_path}`" alt="" v-if="elementObj.poster_path">
      <i class="far fa-images" v-else></i>
      <h2>{{ elementTitle }}</h2>
      <h3>{{ elementOriginalTitle }}</h3>
      <div class="flag-container">
        <img v-if="hasFlag" :src="require(`../assets/img/${elementObj.original_language}.svg`)" alt="" class="flag">
        <p v-else>{{ elementObj.original_language }}</p>
      </div>
      <div class="stars-container"><i
        v-for="n in 5"
        :key="n"
        class="fa-star"
        :class="(n <= starsNbr) ? 'yellow-star fas' : 'far'"
      >
      </i>
      </div>

    </div>
  </li>
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
      flags: ['de', 'en', 'es', 'fr', 'it', 'ja'],
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
    elementTitle(){
      return this.elementObj.title ? this.elementObj.title : this.elementObj.name;
    },
    elementOriginalTitle(){
      return this.elementObj.original_title ? this.elementObj.original_title : this.elementObj.original_name;
    },
    hasFlag(){
      return this.flags.includes(this.elementObj.original_language);
    },
    starsNbr(){
      return Math.ceil(this.elementObj.vote_average / 2);
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
  background-color: rgb(235, 234, 234);
  display: flex;
  flex-direction: column;

  .flag-container{
    
    .flag{
      width: 20px;
    }

    // .stars-container{
    //   color: goldenrod;
    // }

  }

}

</style>