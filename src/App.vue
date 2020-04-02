<template>
  <div>
    <h1>Brewdog App</h1>
    <div class="main-container">
      <beers-list :beers='beers'></beers-list>
      <beer-detail :beer='selectedBeer'></beer-detail>
      <favourite-beers :beer='favouriteBeers'></favourite-beers>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return{
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then((beers) => { 
      // add isFavourite = false to all objects
      this.beers = beers.map((beer) => {
        beer.isFavourite = false;
        return beer
      })    
    })

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })

    eventBus.$on('favourite-beer', (beerId) => {
      console.log(beerId);
      let beer = this.beers.find(beer => beer.id === beerId)
      beer.isFavourite = true;
    })
  },  
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }
}
</script>


<style>

h1{
  color: salmon;
}

</style>