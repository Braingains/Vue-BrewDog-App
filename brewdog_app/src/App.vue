<template lang='html'>
    <div class="main-container">
      <beers-list :beers='beers'> </beers-list>
      <beer-detail :beer='selectedBeer'> </beer-detail>
      <favourite-beers :beer='favourites'> </favourite-beers>
    </div>
</template>

<script>
import { eventBus } from './main.js'
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouriteBeers from './components/FavouriteBeers.vue';

export default {
  name: 'app',
  data (){
    return {
      beers: [],
      selectedBeer : null,
      favourites :[],
      beerToSave : null
    }

  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers);

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    eventBus.$on('beer-to-save', (beer) => {
      this.favourites.push(beer)
    })
  },
  methods: {
    
},
  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail,
    'favourite-beers': FavouriteBeers
    
  }

}
</script>

<style lang="css" scoped>
  .main-container {
    display: flex;
    justify-content: space-between;
  }

</style>