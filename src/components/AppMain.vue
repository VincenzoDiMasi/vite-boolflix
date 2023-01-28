<script>
import {store} from '../store'
export default {
    name: 'AppMain',
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
      <ul> 
        <li v-for="movie in store.movies">
          <figure>
            <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
          </figure>
          <div>
              {{ movie.title }}        
          </div>
          <div>
              {{ movie.original_title }}        
          </div>
          <!-- <img class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`" :alt="movie.original_language">   -->
          <img v-if="movie.original_language === 'it' || movie.original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`" :alt="movie.original_language">
          <div v-else>{{ movie.original_language }}</div>
          <div>
            <div class="empty-star">
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>

              <div class="full-star">
                <i v-for="n in Math.ceil(movie.vote_average / 2)" class="fa-solid fa-star"></i>
              </div>

            </div>        
          </div>
        </li>
      </ul>
    </div>

    <div class="series">
      <h1>Series</h1>
      <ul >
        <li v-for="serie in store.series">
          <figure>
            <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="">
          </figure>
          <div>
              {{ serie.name }}        
          </div>
          <div>
              {{ serie.original_name }}        
          </div>
          <img v-if="serie.original_language === 'it' || serie.original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${serie.original_language}.png`" :alt="serie.original_language">
          <div v-else>{{ serie.original_language }}</div> 
          <div class="empty-star">
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>

              <div class="full-star ">
                <i v-for="n in Math.ceil(serie.vote_average / 2)" class="fa-solid fa-star "></i>
              </div>    
            </div>
        </li>
      </ul>
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