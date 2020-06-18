<template lang="html">
<form v-on:submit.prevent>
  <select v-on:change="handleChange" v-model="selectedBeer">
    <option disabled value =""> Choose a beer...</option>
    <option v-for="(beer,index) in beers" :value="beer" :key ="index"> {{beer.name}}</option>
  </select>
</form>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: "beer-filter-form",
  data(){
    return {
      "selectedBeer": {},
    }
  },
  props: ["beers"],
  methods: {
    handleChange(){
      eventBus.$emit('beer-selected', this.selectedBeer)
    }
  }
}
</script>

<style lang="css" scoped>
form{
  text-align: center;
  margin: 40px 0;
}

select, input[type="text"]{
  font-size: 15px;
}

select {
  margin-left: 20px;
}
</style>
