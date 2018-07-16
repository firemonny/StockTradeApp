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
      <li><a href="#">End Day</a></li>
      <li class="dropdown">
        <a href="#" 
        class="dropdown-toggle" 
        data-toggle="dropdown">Save & Load <span class="caret"></span></a>
        <ul class="dropdown-menu">
          <li><a href="#">Save Data</a></li>
          <li><a href="#">Load Data</a></li>
        </ul>
      </li>
    </ul>
  </div><!-- /.navbar-collapse -->
</nav>
</template>
<script>
export default {
  computed:{
    funds(){
      return this.$store.getters.funds;
    }
  }
}
    
</script>
