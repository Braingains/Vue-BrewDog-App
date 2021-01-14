<template>
    <div>
        <ul v-for="(beer, index) in favourites" :beer= 'beer' :key= 'index'> </ul>
        
    </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'favourite-beers',
    props: ['favourites'],
    methods: {

    }

}
</script>

<style>

</style>