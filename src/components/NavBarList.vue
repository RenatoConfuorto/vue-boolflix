<template>
  <ul>
    <li
      v-for="(element, index) in navBarOptions"
      :key="index"
      :class="{'active' : activeLink == index}"
    >
        <a :href="element.url">{{ element.text }}</a>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'NavBarList',
  data(){
    return{
      activeLink: 0,
      navBarOptions: [
        {
          text: 'home',
          url: '#',
        },
        {
          text: 'film',
          url: '#',
        },
        {
          text: 'serie tv',
          url: '#',
        },
        {
          text: 'originali',
          url: '#',
        },
        {
          text: 'aggiunti di recente',
          url: '#',
        },
        {
          text: 'la mia lista',
          url: '#',
        },
      ],
    }
  },
  
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

ul{
  margin-left: 30px;

  li{
    display: inline-block;
    padding: 0 5px;
    height: $app-header-height;
    line-height: $app-header-height;

    &.active{
      border-bottom: 2px solid $brand-primary-color;
    }

    a{
      color: white;
      text-decoration: none;
      text-transform: capitalize;
    }
  }
}
</style>