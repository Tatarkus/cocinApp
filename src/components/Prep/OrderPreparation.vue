<template>
  <div class="dish-container">
    <dish :dish-number="n" v-for="n in 10" :key="n"/>
  </div>
</template>

<script>
import Dish from "components/Prep/Dish";
export default {
name: "OrderPreparation",
  components: {Dish}
}
</script>

<style scoped>

</style>
