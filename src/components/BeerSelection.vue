<template>
    <div class="beerselection row">
        <div class="jumbotron col-xs-12">
            <h2><span class="glyphicon glyphicon-list-alt"> Beers List</span></h2>
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
             beer: ''
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
        this.$axios.get('https://api.punkapi.com/v2/beers?per_page=80')
              .then(response => {
                  this.beers = response.data;
              });
     }
 }
</script>

<style>

</style>
