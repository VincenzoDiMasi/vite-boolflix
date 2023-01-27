<script >
import axios from 'axios'
import {store} from './store'
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  components : {AppHeader, AppMain},
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
          return
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
  <app-main></app-main>

  
</template>

<style lang="scss">

</style>
