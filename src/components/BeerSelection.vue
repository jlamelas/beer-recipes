<template>
    <div class="beerselection">
        <div class="jumbotron">
            <h2><span class="glyphicon glyphincon-list-alt">Beers List</span></h2>
            <h4>Select a beer</h4>
            <select class="form-control" v-on:change="beerChanged">
                <option value="">Please, select a beer...</option>
                <option v-for="beer in beers" v-bind:value="beer.id">{{beer.name}}</option>
            </select>
        </div>
    </div>
</template>

<script>
 export default {
     name: 'beerselection',
     data () {
         return {
             beers: [],
             beer: null
         }
     },
     methods: {
         beerChanged (e) {
             for (var i = 0; i < this.beers.length; i++) {
                 if (this.beers[i].id == e.target.value) {
                     this.beer = this.beers[i];
                 }
             }
             this.$emit('beerChanged', e.target.value);
         }
     },
     created () {
        axios.get('https://api.punkapi.com/v2/beers?per_page=100')
              .then(reponse => {
                  this.beers = response.data;
              });
     }
 }
</script>

<style>

</style>
