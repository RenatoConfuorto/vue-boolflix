<template>
  <li class="card">
    <div class="card-content">
      <div class="card-front">
        <img :src="`http://image.tmdb.org/t/p//w500/${elementObj.poster_path}`" alt="" v-if="elementObj.poster_path">
        <div v-else class="else-front">
          <i class="far fa-images"></i>
        </div>
      </div>

      <div class="card-back">
        <p class="text-info">Titolo: <span>{{ elementTitle }}</span></p>
        <p class="text-info">Titolo originale: <span>{{ elementOriginalTitle }}</span></p>
        <p class="text-info">Voto: 
          <span class="stars-container">
            <i
            v-for="n in 5"
            :key="n"
            class="fa-star"
            :class="(n <= starsNbr) ? 'yellow-star fas' : 'far'"
          >
            </i>
          </span>
        </p>
        <div class="overview">
          <p class="text-info">Overview: <span v-if="elementObj.overview">{{ elementObj.overview }}</span>
          <span v-else>Descrizione non disponibile</span>
          </p>
        </div>
        <div class="flag-container">
          <img v-if="hasFlag" :src="require(`../assets/img/${elementObj.original_language}.svg`)" alt="" class="flag">
          <p v-else>{{ elementObj.original_language }}</p>
        </div>
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
@import "../style/variables.scss";

.card{
  position: relative;
  color: white;
  width: calc(25% - 6px);
  margin: 3px;
  margin-bottom: 6px;
  perspective: 500px;
  align-self: stretch;

  &:hover .card-content{
    transform: rotateY(180deg);
  }

  &-content{
    position: relative;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 1s;
  } 
  

  &-front,
  &-back{
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
  }

  &-front{
    text-align: center;
    overflow: hidden;
    background-color: transparent;

    img{
      height: 100%;
      object-fit: cover;
    }

    .else-front{
      background-color: $brand-secondary-color;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;

      i{
      font-size: 5rem;
    }
    }
  }

  &-back{
    background-color: $brand-secondary-color;
    transform: rotateY(180deg);
    position: absolute;
    padding: 10px;
    top: 0;

    display: flex;
    flex-direction: column;
    
    .text-info{
      font-weight: 600;
      margin-bottom: 2px;

      span{
        font-weight: 100;
      }
    }

    .overview{
      flex-grow: 1;
      overflow-y: auto;

      //scrollbar
      &::-webkit-scrollbar {
        width: 4px;
      }
      &::-webkit-scrollbar-track {
        background: $brand-secondary-color;
        border-radius: 5px;
      }
      &::-webkit-scrollbar-thumb {
        background: $brand-primary-color; 
        border-radius: 5px;
      }
      &::-webkit-scrollbar-thumb:hover {
        background: #555;
      }
      //fine scrollbar

      span{
        font-size: .8rem;
      }
    }

    .flag-container{

      .flag{
        width: 20px;
      }
    }
  }


}

</style>