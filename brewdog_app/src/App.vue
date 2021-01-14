<template lang='html'>
  <p>helllloooo</p>
</template>

<script>
export default {
  name: 'app',
  data (){
    return {
      beers: [],
    }

  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers);
  }

}
</script>

<style>

</style>