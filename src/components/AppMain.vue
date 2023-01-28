<script>
import {store} from '../store'
import ProductCard from './ProductCard.vue';
export default {
    name: 'AppMain',
    components: {ProductCard},
    data () {
        return {
            store,
            
            
        }
    }  
    }
   
</script>

<template>
   <main>
        <div class="container d-flex align-items-center">
            <section v-if="store.movies.length || store.series.length" class="py-3">
                <div class="movies">
                    <h1 class="text-white">Movies</h1>
                        <product-card v-for="movie in store.movies" :product="movie" key=""></product-card>
                </div>

                <div class="series">
                    <h1 class="text-white">Series</h1>
                        <product-card v-for="serie in store.series"  :product="serie"></product-card>
                </div>
            </section>

            <h1 v-else class="text-white py-3 ">
                Cosa vuoi guardare?
            </h1>

        </div>
      

    </main>

</template>

<style lang="scss" scoped>
   main {
      background-color: grey;
      min-height: calc(100vh - 80px);
    }


</style>