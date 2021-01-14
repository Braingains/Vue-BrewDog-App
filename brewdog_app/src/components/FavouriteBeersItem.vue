<template>
    <li v-if='beer'> {{beer.name}}</li>    
</template>

<script>
export default {
  name: "favourite-beers-item",
  props: ["beer"],
};
</script>

<style>
</style>