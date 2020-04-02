<template lang="html">
  <div>
      <h2>Fave Beers Live Here</h2>
    <ul>
      <list-item v-for="(beer, index) in favouriteBeers" 
        :beer="beer" 
        :key="index">{{ beer }}</list-item>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    name: 'favourite-beers',
    props: ['favouriteBeers'],
    components: {
    "list-item": ListItem
  }

}
</script>

<style scoped>

</style>