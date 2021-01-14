<template>
    <div v-if="beer">
        <p>{{beer.tagline}}</p>
        <li>
        {{ beer.ingredients }}
        </li>
        <button v-on:click = 'saveBeer' > Add to Favourites </button>
    </div>
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'beer-detail',
    props: ['beer'],
    methods: {
        saveBeer: function(){
            eventBus.$emit('beer-to-save', this.beer)
        }
    }

}
</script>

<style>

</style>