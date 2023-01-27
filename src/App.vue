<script >
import axios from 'axios'
import {store} from './store'
export default {
  data (){
    return {
      store,
      searchProduct: '',
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=a',
      movies: [],
      series: []
      
    }
  },
  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        this.movies = res.data.results;
        this.series = []
      });
      },
      fetchSeries(url) {
        axios.get(url)
        .then((res) => {
        this.series = res.data.results;
      });
      },
      onTypeSearch(){
        const movieUri = `https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=${this.searchMovie}`
        this.fetchMovie(movieUri);
        const seriesUri = `https://api.themoviedb.org/3/search/tv?api_key=00ab33acaa22d58af366e888c3e4fe95&query=${this.searchMovie}`
        this.fetchSeries(seriesUri)
      },
      cleanInput(){
        if (this.searchMovie === ''){
          this.movies = []
        }
      }
  },
}
//   created() {
//     this.fetchMovie(this.apiUri);
//   }
// }
</script>

<template>
  <h1 class="m-4">
    BOOLFLIX
  </h1>
  <div class="input-group flex-nowrap w-25">
    <input @keyup="cleanInput" @keyup.enter="onTypeSearch" v-model.trim="searchMovie" type="text" class="form-control" placeholder="Cerca" aria-label="Username" aria-describedby="addon-wrapping">
    <button @click="onTypeSearch" class="btn btn-danger">Cerca</button>
  </div>

  <div class="movies">
      <h1>Movies</h1>
      <ul> 
        <li v-for="movie in movies">
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
