<template>
    <nav class="navbar navbar-default navbar-static-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <router-link to="/" activeClass="navbar-brand">Stock Trader</router-link>
        </div>
        <div id="navbar" class="navbar-collapse collapse">
          <ul class="nav navbar-nav">
              <li> <router-link to="/portfolio" activeClass="active">Portfolio</router-link></li>
              <li> <router-link to="/stocks" activeClass="active">Stocks</router-link> </li>
          </ul>
          <strong class="navbar-text navbar-right">{{funds | currency}}</strong>
          <ul class="nav navbar-nav navbar-right">
            <li><a href="#contact"  @click="endDay">End Day</a></li>
            <li class="dropdown" :class="{open: isDropdownOpen}">
              <a href="#"
              class="dropdown-toggle"
              data-toggle="dropdown"
              role="button"
              aria-haspopup=""
              @click="dropdown"
              aria-expanded="false">Save & Load <span class="caret"></span></a>
              <ul class="dropdown-menu">
                <li><a href="#" @click="saveData">Save Data</a></li>
                <li><a href="#" @click="loadData">Load Data</a></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>
<script>
  import {mapActions} from 'vuex';
  export default {
    data() {
      return {
         isDropdownOpen: false
      }
    },
    computed: {
      funds() {
         return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions({
        randomizeStocks: 'randomizeStocks',
        fetchData: 'loadData'
      }),
      endDay() {
         this.randomizeStocks();
      },
      dropdown() {
        this.isDropdownOpen = !this.isDropdownOpen;
      },
      saveData() {
         const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
         }
         this.$http.put('data.json', data);
      },
      loadData() {
         this.fetchData();
      }
    }
  }
</script>
