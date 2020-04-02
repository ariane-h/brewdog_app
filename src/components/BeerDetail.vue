<template>
  <div v-if="beer">
      <h3>{{ beer.name }}</h3>
      
  </div>
</template>

<script>

import { eventBus } from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style scoped>

</style>