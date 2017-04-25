<template>
    
</template>

<script>
 export default {
     name: 'beerdescription',
     props: ['beer'],
     data () {
         return {
             description: null
         }
     },
     methods: {
         updateBeer (beer) {
             this.$axios.get('https://api.punkapi.com/v2/beers?beer_name=' + beer)
                 .then(response => {
                     this.description = response.data;
                 });
         }
     },
     created () {
         this.updateBeer(this.beer);
     }
 }
</script>

<style>
 
</style>
