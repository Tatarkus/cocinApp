<template class="">
  <q-page class="flex">.

    <div
    class="col bg-dark">
      <div
      class="orderprep" v-if="dataFetched">
        <!-- Right drawer that display all the orders from the selected table order-->
        <OrderPreparation @mesa-servida="served" :key="order.id" v-for="order in prepOrders" :order="order"/>
      </div>

      <div class="orderqueue" v-if="dataFetched">
      <!-- Right drawer that display all the orders from the selected table order-->
        <OrderQueue @load-dishes="loadDishes" :tableOrders="this.tableOrders"></OrderQueue>

      </div>
    </div>
  </q-page>
</template>

<script>
import OrderDetail from "components/Detail/OrderDetail";
import OrderPreparation from "components/Prep/OrderPreparation";
import OrderQueue from "components/Queue/OrderQueue";
import axios from "axios";
export default {
  name: 'PageIndex',
  components: {OrderQueue, OrderPreparation},
  methods: {
    async fetchData(){
      let response = await axios.get('http://localhost:8082/kitchenOrders/');
      this.tableOrders=response.data.orders;
      for (let i = 0; i < this.tableOrders.length; i++) {
        let res = await axios.get('http://localhost:8082/requestedDishes/'+this.tableOrders[i].id,
          {crossDomain: true})
        this.tableOrders[i].dishes = res.data
      }
      this.dataFetched=true


    },
    loadDishes(order){
      this.prepOrders.push(order)
      this.tableOrders.forEach(
        tOrder =>
      {
        if(tOrder.id == order.id)
        {
          this.tableOrders.splice(this.tableOrders.indexOf(tOrder),1)
        }
      })
    },
    served(orden){
      this.prepOrders.forEach(
        prep => {
          if (prep.id == orden.id) {
            this.prepOrders.splice(this.prepOrders.indexOf(prep),1)
          }
        })
    },
  },
  data() {
    return {
      tableOrders:{},
      prepOrders:[],
      dataFetched:false
    }
  },
  created( ) {
    this.fetchData();
  }

}
</script>

<style>
.orderprep
  {
    height:70vh ;
    background-color: dark;
  }
.orderqueue
  {
    height: 26.5vh;
    background-color: #1976D2;
  }

</style>
