<template lang="html">
  <ul class="nav nav-tabs">
  <li class="nav-item">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>
  </li>
  <li class="nav-item">
      <router-link to="/Portfolio" class="navbar-brand" activeClass="active" tag="li"><a>Portfolio</a></router-link>
  </li>
  <li class="nav-item">
    <router-link to="/stocks" class="navbar-brand" activeClass="active" tag="li"><a>Stocks</a></router-link>
  </li>

  <li class="nav-item">
      <a href="#" class="navbar-brand" @click='endDay'>End Day</a>
  </li>
  <li class="nav-item dropdown" :class="{open: isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
    <a class="nav-link dropdown-toggle navbar-brand" data-toggle="dropdown" href="#" role="button" aria-haspopup="true" aria-expanded="false">Save & Load</a>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Save Data</a>
      <a class="dropdown-item" href="#">Load Data</a>
    </div>
    <strong class="navbar-brand"> Funds: {{ funds | currency }}</strong>
  </li>

</ul>

</template>

<script>
import {mapActions} from 'vuex';

export default {
  data () {
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
    ...mapActions([
      'randomizeStocks'
    ]),
    endDay() {
      this.randomizeStocks();
    }
  }
}
</script>

<style lang="css">
</style>
