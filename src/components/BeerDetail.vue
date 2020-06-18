<template lang="html">
  <div v-if="beer" id="beerDetail">
    <div id ="detailWrapper">
      <h2>{{beer.name}}</h2>
      <div id="flexWrapper">
        <div id = "right">
          <img :src="beer.image_url">
        </div>
        <div id="left">
          <p><span> ABV</span>: {{beer.abv}}</p>
          <p><span> Description</span>: {{beer.description}}</p>
          <p><span> Food Pairing</span>:</p>
            <ul v-for="food_pairing in beer.food_pairing">
              <li>{{beer.food_pairing}}</li>
            </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'beer-detail',
  data(){
    return {
      beer:null
    }
  },
  mounted(){
    eventBus.$on('beer-selected', (beer) =>{
      this.beer = beer
    })
  }
}
</script>


<style lang="css" scoped>

#beerDetail {
    box-sizing: border-box;
    height: 400px;
    width: 60%;
    background: #eee;
    color: #222;
    padding: 10px;
    border: 1px solid #ccc;
    margin: 0 auto;
  }

  #detailWrapper {
    box-sizing: border-box;
    background: #fff;
    padding: 10px;
    height: 100%;
    border-radius: 3px;
  }

  #flexWrapper {
    display: flex;
    justify-content: space-between;
  }

  #left, #right {
    width: 50%;
  }

  #right img {
    width:30%
  }
</style>
