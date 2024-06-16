<script>
import axios from 'axios';
import MovieList from './components/MovieList.vue';
import SearchBar from './components/SearchBar.vue';

export default {
  name: 'App',
  components: {
    MovieList,
    SearchBar
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    async fetchMovies(query) {
      try {
        const apiKey = import.meta.env.VITE_TMDB_API_KEY;
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
