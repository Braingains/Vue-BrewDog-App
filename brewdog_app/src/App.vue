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
      beers3: [],
      beers4: [],
      beers5: [],
      selectedBeer : null,
      favourites :[],
      beerToSave : null
    }

  },
  mounted(){
// Promise.all([promise1, promise2, promise3]).then((values) => {
  // console.log(values);
// });
    


    // fetch('https://api.punkapi.com/v2/beers?page=1&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers1 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers2 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=3&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers3 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=4&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers4 = beers);

    // fetch('https://api.punkapi.com/v2/beers?page=5&per_page=80')
    // .then(res => res.json())
    // .then(beers => this.beers5 = beers);

    
    this.getAllBeers();
    

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
    //beer from favourites is taken from eventsBus,
    //we get indexOf that beer,
    //we give that index to .splice and remove (1) item at that index

  },
  methods: {

    getAllBeers: function(){
      const promises = [1,2,3,4,5].map(number =>{
        return fetch(`https://api.punkapi.com/v2/beers?page=${number}&per_page=80`)
        .then(res => res.json())
      })
      console.log(promises);
      Promise.all(promises)
        .then(data => {
          const beerInfo = data.reduce((beers, beersToAdd) => {
            return beers.concat(beersToAdd)
          }, [])

          this.beers = beerInfo
        })
        

    }
    
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
    background-image: url("https://media3.giphy.com/media/V6vYGxjArFFde/giphy.gif?cid=ecf05e4712qiv49f8u8s00362p60h74i5rwtfcr6l8hh7cdt&rid=giphy.gif");
    background-color: #5229037b;
    background-repeat:no-repeat;
    background-size:contain;
    color: lemonchiffon; 
    
  }
 
</style>