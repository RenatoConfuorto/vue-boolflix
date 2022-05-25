<template>
  <div class="card-container">
    <ElementCard  v-for="(element, index) in elementArray" :key="index" :elementObj="element"/>
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
  display: flex;
  flex-wrap: wrap;
}

</style>