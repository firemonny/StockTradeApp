<template>
    <nav class="navbar navbar-default" role="navigation">
    <div class="navbar-header">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>
    </div>


  <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
    <ul class="nav navbar-nav">
      <router-link to="/portfolio" tag="li"><a>Portfolio</a></router-link>
      <router-link to="/stocks" tag="li" activeClass="active"><a>Stock</a></router-link>
    </ul>
    <strong class="navbar-text navbar-right">Funds: {{funds}}</strong>
    <ul class="nav navbar-nav navbar-right">
      <li><a @click="endDay">End Day</a></li>
      <li class="dropdown" :class="{open: isDropdownOPen}" @click="isDropdownOPen = !isDropdownOPen">
        <a href="#" 
        class="dropdown-toggle" 
        data-toggle="dropdown">Save & Load <span class="caret"></span></a>
        <ul class="dropdown-menu">
          <li><a href="#" @click="saveData">Save Data</a></li>
          <li><a href="#" @click="loadData">Load Data</a></li>
        </ul>
      </li>
    </ul>
  </div><!-- /.navbar-collapse -->
</nav>
</template>
<script>
import { mapActions } from 'vuex';
export default {
  data(){
    return{
      isDropdownOPen:false
    }
  },
  computed:{
    funds(){
      return this.$store.getters.funds;
    }
  },
  methods:{
    ...mapActions({
      randomizeStocks: 'randomizeStocks',
      fetchData: 'loadData'
    }),
    endDay(){
      this.randomizeStocks();
          },
    saveData(){
      const data = {
        funds: this.$store.getters.funds,
        stockPortfolio: this.$store.getters.stockPortfolio,
        stocks: this.$store.getters.stocks
      };
      this.$http.put('data.json',data);
    },
    loadData(){
      this.fetchData();
    }
  }
}
    
</script>
