<template lang='html'>
    <div class="main-container">
      <beers-list :beers='beers'> </beers-list>
      <beer-detail :beer='selectedBeer'> </beer-detail>
      <favourite-beers :favouriteBeers='favourites'> </favourite-beers>
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
      beers1: [],
      beers2: [],
      selectedBeer : null,
      favourites :[],
      beerToSave : null
    }

  },
  mounted(){
// Promise.all([promise1, promise2, promise3]).then((values) => {
  // console.log(values);
// });
    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    .then(res => res.json())
    .then(beers => this.beers = beers);
    // Promise.all([fetch('https://api.punkapi.com/v2/beers?page=1&per_page=80'), fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80'),
    // fetch('https://api.punkapi.com/v2/beers?page=3&per_page=80'),
    // fetch('https://api.punkapi.com/v2/beers?page=4&per_page=80')]) 
    // .then(res => res.json())
    // .then(beers => this.beers1 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers2 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=3&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers.push(beers));

    // fetch('https://api.punkapi.com/v2/beers?page=4&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers.push(beers));

    // fetch('https://api.punkapi.com/v2/beers?page=5&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers.push(beers));

    // function (beers1, beers2){
    //   beers.shift(beers1, beers2)
    // }

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    eventBus.$on('beer-to-save', (beer) => {
      if(!this.favourites.includes(beer)){
        this.favourites.push(beer)
      }
    })
    eventBus.$on('beer-to-remove', (beer) => {
      const index = this.favourites.indexOf(beer)
      this.favourites.splice(index, 1)
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