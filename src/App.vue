<template lang="html">
  <div>
    <h1>BREWDOG BEER MENU </h1>
    <beer-filter-form :beers="beers"> </beer-filter-form>
    <beer-detail />
  </div>
</template>

<script>
import BeerFilterForm from './components/BeerFilterForm.vue'
import BeerDetail from './components/BeerDetail.vue'

export default {
  data(){
    return {
      beers: [],
    }
  },
  components: {
    "beer-filter-form":BeerFilterForm,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers)
  }
}

</script>

<style lang="css" scoped>

h1{
  font-family: New-Grotesk-Square;
  font-weight:500;
  color: #000;
  text-align: center;
}
</style>
