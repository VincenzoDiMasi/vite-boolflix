<script >
import axios from 'axios'
import {store} from './store'
export default {
  data (){
    return {
      store,
      searchMovie: '',
      apiUri: 'https://api.themoviedb.org/3/search/movie?api_key=00ab33acaa22d58af366e888c3e4fe95&query=all',
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
  },
  created() {
    this.fetchMovie(this.apiUri);
  }
}
</script>

<template>
  <h1 class="m-4">
    AAAAA
  </h1>
  <div class="input-group flex-nowrap w-25">
    <input v-model="searchMovie" type="text" class="form-control" placeholder="Cerca film" aria-label="Username" aria-describedby="addon-wrapping">
  </div>

  <ul>
    <li v-for="movie in movies">
      <div>
          {{ movie.title }}        
      </div>
      
    </li>
  </ul>
</template>

<style >

</style>
