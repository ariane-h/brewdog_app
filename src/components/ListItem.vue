<template lang="html">
    <li v-on:click="handleClick" :class="favouriteClass">{{beer.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer )
    }
  },
  computed: {
        favouriteClass: function(){
            return this.beer.isFavourite ? "favourite" : "not_favourite";
        }
    }
}
</script>

<style scoped>

    .not_favourite{
        
    }

    .favourite{
        background-color: lightcyan;
    }

</style>