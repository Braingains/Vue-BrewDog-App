<template lang='html'>
    <div>
      <beers-list :beers='beers'> </beers-list>
    </div>
</template>

<script>
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue';
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
  },
  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail
  }

}
</script>

<style>

</style>