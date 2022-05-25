<template>
  <div>
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

div{
  background-color: lightgrey;
  display: flex;
  flex-wrap: wrap;
}

</style>