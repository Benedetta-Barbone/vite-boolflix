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
      media: []
    };
  },
  methods: {
    async fetchMedia(query) {
      try {
        const apiKey = 'e9b84d50153bb26143d63dd4aa30fb8a';
        
        const [moviesResponse, tvShowsResponse] = await Promise.all([
          axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
              api_key: apiKey,
              query: query,
              language: 'it-IT'
            }
          }),
          axios.get('https://api.themoviedb.org/3/search/tv', {
            params: {
              api_key: apiKey,
              query: query,
              language: 'it-IT'
            }
          })
        ]);

        const movies = moviesResponse.data.results.map(item => ({
          ...item,
          media_type: 'movie'
        }));

        const tvShows = tvShowsResponse.data.results.map(item => ({
          ...item,
          media_type: 'tv'
        }));

        this.media = [...movies, ...tvShows];
      } catch (error) {
        console.error('Error fetching media:', error);
      }
    }
  }
}
</script>


<template>
  <div id="app">
    <SearchBar @search="fetchMedia" />
    <MovieList :movies="media" />
  </div>
</template>
