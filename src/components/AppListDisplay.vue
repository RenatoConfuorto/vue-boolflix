<template>
  <div class="card-container">
    <ul>
      <ElementCard  v-for="(element, index) in elementArray" :key="index" :elementObj="element"/>
    </ul>
  </div>
</template>

<script>
import ElementCard from "./ElementCard.vue";

export default {
  components: {
    ElementCard,
  },
  props: {
    elementArray: Array,
  }
}
</script>

<style lang="scss" scoped>

.card-container{
  
  ul{
    display: flex;
    flex-wrap: wrap;
  }
}

</style>