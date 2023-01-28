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
   <div class="movies">
      <h1>Movies</h1>
      <ProductCard v-for="movie in store.movies" :product="movie" key=""></ProductCard>
    </div>

    <div class="series">
      <h1>Series</h1>
      <ProductCard v-for="serie in store.series" :product="serie" ></ProductCard>
    </div>

</template>

<style lang="scss" scoped>
   .flag {
  height: 18px;
}

.poster {
    height: 300px;
    cursor: pointer;
}

.empty-star {
    position: relative;
  }
  .full-star {
    position: absolute;
    top: 0;
    left: 0;
    color: #dc3545;
  }


</style>