<template>
    <div>
        <ul> 
            <favourite-beers-item v-for="(beer, index) in favouriteBeers" :beer= 'beer' :key= 'index'>
            </favourite-beers-item>
         </ul>
        
    </div>
</template>

<script>
import FavouriteBeersItem from './FavouriteBeersItem.vue'
import { eventBus } from '../main.js'
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers'],
    methods: {

    },
    components: {
        'favourite-beers-item' : FavouriteBeersItem
    }

}
</script>

<style>

</style>