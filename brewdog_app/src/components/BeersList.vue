<template>
    <div>
        <ul>
            <beer-list-item v-for="(beer, index) in beers" :beer='beer' :key='index'>  </beer-list-item>
        </ul>

    </div>
</template>

<script>
import BeersListItem from './BeerListItem.vue';

export default {
    name: 'beers-list',
    props: ['beers'],
    

    components: {
        'beer-list-item' : BeersListItem
    }

}
</script>

<style>

</style>