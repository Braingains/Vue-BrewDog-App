<template>
    <li v-if='beer'> {{beer.name}}
        <button v-on:click="removeFromFavourites"> Remove </button>
        </li>    
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: "favourite-beers-item",
  props: ["beer"],
  methods: {
    removeFromFavourites: function(){
      eventBus.$emit('beer-to-remove', this.beer)
    }
  }
};
</script>

<style>
</style>