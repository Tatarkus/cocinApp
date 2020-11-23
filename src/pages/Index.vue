<template class="">
  <q-page class="flex flex-center">.
    <!-- Right drawer that display all the orders from the selected table order-->
    <OrderDetail></OrderDetail>

    <div
    class="col">
      <div
      class="orderprep row1">
        <!-- Right drawer that display all the orders from the selected table order-->
        <OrderPreparation></OrderPreparation>
      </div>

      <div class="orderqueue row2">
      <!-- Right drawer that display all the orders from the selected table order-->
        <OrderQueue></OrderQueue>

      </div>
    </div>
  </q-page>
</template>

<script>
import OrderDetail from "components/Detail/OrderDetail";
import OrderPreparation from "components/Prep/OrderPreparation";
import OrderQueue from "components/Queue/OrderQueue";
export default {
  name: 'PageIndex',
  components: {OrderQueue, OrderPreparation, OrderDetail}
}
</script>

<style>
.row1 {
  min-height: 66vh;
  min-width: 100vh;
  background-color: crimson;
}
.row2{
  min-width: 100px;
  min-height: 30vh;
  background-color: #1976D2;
}

</style>
