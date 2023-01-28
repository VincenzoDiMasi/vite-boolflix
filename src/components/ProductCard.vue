
<script>
    export default {
        name: 'ProductCard',
        props: {
            poster_path: String,
            title: String,
            original_title: String,
            original_language: String,
            vote_average: String,
            name: String,
            original_name: String,
        }
    }
</script>

<template>
    <figure>
        <img :src="`https://image.tmdb.org/t/p/w342/${poster_path}`" :alt="title">
    </figure>   
    
    <div>
        {{ title || name }}        
    </div>
    <div>
       {{ original_title || original_name }}        
    </div>
    <img v-if="original_language === 'it' || original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${original_language}.png`" :alt="serie.original_language">
    <div v-else>{{ original_language }}</div> 

    <div>    
        <div class="empty-star">
        <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>
            <i class="fa-regular fa-star"></i>

            <div class="full-star">
                <i v-for="n in Math.ceil(vote_average / 2)" class="fa-solid fa-star"></i>
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