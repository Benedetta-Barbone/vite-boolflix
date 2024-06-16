<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';

export default {
  name: 'App',
  components: {
    SearchBar,
    MovieList
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    async fetchMovies(query) {
      try {
        const apiKey = 'e9b84d50153bb26143d63dd4aa30fb8a'; // API key definita direttamente
        const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: apiKey,
            query: query,
            language: 'it-IT'
          }
        });
        this.movies = response.data.results;
      } catch (error) {
        console.error('Error fetching movies:', error);
      }
    }
  }
}
</script>


<template>
  <div id="app">
    <SearchBar @search="fetchMovies" />
    <MovieList :movies="movies" />
  </div>
</template>
