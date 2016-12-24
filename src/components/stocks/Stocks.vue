<template>
  <div>
    <app-stock v-for="stock in stocks" :stock="stock"></app-stock>
  </div>
</template>
<script>
import Stock from './Stock.vue';
export default {
  name: 'stock',
  components: {
     appStock: Stock
  },
  computed: {
    stocks() {
      return this.$store.getters.stocks;
    }
  }
}
</script>
