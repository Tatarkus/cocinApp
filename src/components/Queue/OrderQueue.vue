<template>
  <div
    class>
  <TableOrder v-for="n in 5" :key="n"/>
  </div>
</template>

<script>
import TableOrder from "components/Queue/TableOrder";
export default {
name: "OrderQueue",
  components: {TableOrder}
}
</script>

<style scoped>

</style>
