<template>
  <li>  
    {{ beer.name }}

    </li>
</template>

<script>
export default {
    name: 'beer-list-item',
    props: ['beer']

}
</script>

<style>

</style>