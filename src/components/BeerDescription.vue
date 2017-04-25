<template>
    <div class="beerdescription">
        <div class="container">
            <div class="media">
                <div class="media left">
                    <img class="media-object" alt="" v-bind:src="description.image_url"/>
                </div>
                <div class="media-body">
                    <div class="media-heading">
                        <h4>{{description.name}} <br/>
                            <small>{{description.tagline}}</small>
                        </h4>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
 export default {
     name: 'beerdescription',
     props: ['beer'],
     data () {
         return {
             description: ''
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
     },
     watch: {
         beer (val) {
             this.updateBeer(val);
         }
     }
 }
</script>

<style>

</style>
