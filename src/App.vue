<template>
    <div class="container" id="app">
        <BeerSelection v-on:beerChanged="beerChanged"></BeerSelection>
        <BeerDescription v-bind:beer="beer"></BeerDescription>
    </div>
</template>

<script>
 import BeerSelection from './components/BeerSelection'
 import BeerDescription from './components/BeerDescription'

 export default {
     name: 'app',
     components: {
         BeerSelection,
         BeerDescription
     },
     data () {
         return {
             beer: null
         }
     },
     methods: {
         beerChanged (beer) {
             this.beer = beer;
         }
     }
 }
</script>

<style>
 #app {
     padding-top: 20px;
 }
</style>
