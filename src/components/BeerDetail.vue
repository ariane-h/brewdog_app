<template lang="html">
  <div v-if="beer">
      <h3>Name: {{ beer.name }}</h3>
      <p>Tagline: {{ beer.tagline }}</p>
      <p>ABV: {{ beer.abv }}%</p>

      <img :src="beer.image_url" :alt="beer.name">

      <p>Description: {{ beer.description }}</p>
      <p>Food Pairings:</p>
      <ul>
        <li v-for="(food, index) in beer.food_pairing" :food="food" :key="index">{{ food }}</li>
      </ul>

      <button type="button" v-on:click="handleButtonClick">Add to Favourites</button>


      
  </div>
</template>

<script>

import { eventBus } from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beer'],
    methods: {
    handleButtonClick(){
      eventBus.$emit('favourite-beer', this.beer.id )
    }
  }
}
</script>

<style scoped>

</style>