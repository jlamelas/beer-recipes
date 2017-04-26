<template>
    <div class="beerdescription">
        <div class="media">
            <div class="media-left">
                <img class="media-object" alt="" v-bind:src="description.image_url"/>
            </div>
            <div class="media-body">
                <div class="media-heading">
                    <h4>{{description.name}} <br/>
                        <small>{{description.tagline}}</small>
                    </h4>
                </div>
                <p>
                    {{description.description}}
                </p>
                <h4 v-if="description.food_pairing">Food pairing</h4>
                <p v-for="food in description.food_pairing">
                    {{food}}.
                </p>
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
             description: []
         }
     },
     methods: {
         updateBeer (beer) {
             this.$axios.get('https://api.punkapi.com/v2/beers?ids=' + beer)
                 .then(response => {
                     this.description = response.data[0];
                 });
         }
     },
     created () {
         this.updateBeer(this.beer);
     },
     watch: {
         beer: function (val) {
             this.updateBeer(val);
         }
     }
 }
</script>

<style scoped>
 .media-object {
     width: 128px;
     padding: 10px;
 }
</style>
