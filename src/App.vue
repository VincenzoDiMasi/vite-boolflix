<script >
import axios from 'axios'
import {store} from './store'
import AppHeader from './components/AppHeader.vue'
export default {
  components : {AppHeader},
  data (){
    return {
      store,
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=a',
      
    }
  },
  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        store.movies = res.data.results;
        store.series = []
      });
      },
      fetchSeries(url) {
        axios.get(url)
        .then((res) => {
        this.series = res.data.results;
      });
      },
      onProductSearch(searchProduct){
        const movieUri = `https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=${this.searchProduct}`
        this.fetchMovie(movieUri);
        const seriesUri = `https://api.themoviedb.org/3/search/tv?api_key=00ab33acaa22d58af366e888c3e4fe95&query=${this.searchProduct}`
        this.fetchSeries(seriesUri)
      },
      cleanInput(searchProduct){
        if (searchProduct === ''){
          store.movies = []
          store.series = []
        }
      },
  },
}
//   created() {
//     this.fetchMovie(this.apiUri);
//   }
// }
</script>

<template>
  
  <app-header @product-search="onProductSearch" @clean-input="cleanInput"></app-header>
  <div class="movies">
      <h1>Movies</h1>
      <ul> 
        <li v-for="movie in store.movies">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
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
              {{ movie.vote_average }}        
          </div>
        </li>
      </ul>
    </div>

    <div class="series">
      <h1>Series</h1>
      <ul>
        <li v-for="serie in series">
          <figure>
            <img :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="">
          </figure>
          <div>
              {{ serie.name }}        
          </div>
          <div>
              {{ serie.original_name }}        
          </div>
          <img v-if="serie.original_language === 'it' || serie.original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${serie.original_language}.png`" :alt="serie.original_language">
          <div v-else>{{ serie.original_language }}</div> 
          <div>
              {{ serie.vote_average }}        
          </div>
        </li>
      </ul>
    </div>
</template>

<style lang="scss">
.flag {
  height: 18px;
}

</style>
