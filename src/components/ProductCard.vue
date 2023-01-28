
<script>
    export default {
        name: 'ProductCard',
        props: {
            poster_path: String,
            title: String,
            original_title: String,
            original_language: String,
            vote_average: Number,
            name: String,
            original_name: String,
            product: Object,
        }
    }
</script>

<template>
    <div class="col mb-3">
       
        <figure>
            <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="title">
        </figure>   
        
        <div>
            {{ product.title || product.name }}        
        </div>
        <div>
        {{ product.original_title || product.original_name }}        
        </div>
        <img v-if="product.original_language === 'it' || product.original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${product.original_language}.png`" :alt="product.original_language">
        <div v-else>{{ product.original_language }}</div> 

        <div>    
            <div class="empty-star">
            <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>
                <i class="fa-regular fa-star"></i>

                <div class="full-star">
                    <i v-for="n in Math.ceil(product.vote_average / 2)" class="fa-solid fa-star"></i>
                </div>
            </div>

        </div>
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