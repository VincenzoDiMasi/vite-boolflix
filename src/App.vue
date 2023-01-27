<script >
import axios from 'axios'
import {store} from './store'
export default {
  data (){
    return {
      store,
      searchMovie: '',
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=a',
      movies: []
      
    }
  },
  methods: {
      fetchMovie(url) {
        axios.get(url)
        .then((res) => {
        this.movies = res.data.results;
      });
      },
      onTypeSearch(){
        const apiUri = `https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=${this.searchMovie}`
        this.fetchMovie(apiUri)
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

  <ul>
    <li v-for="movie in movies">
      <div>
          {{ movie.title }}        
      </div>
      <div>
          {{ movie.original_title }}        
      </div>
      <div>
        <img class="img-fluid flag" :src="`/src/assets/img/${movie.original_language}.png`">       
      </div>
      <div>
          {{ movie.vote_average }}        
      </div>
    </li>
  </ul>
</template>

<style lang="scss">
.flag {
  height: 18px;
}

</style>
