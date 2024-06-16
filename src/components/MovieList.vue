

<script>
import MovieCard from './MovieCard.vue';

export default {
  name: 'MovieList',
  components: {
    MovieCard
  },
  props: {
    movies: {
      type: Array,
      required: true
    }
  }
}
</script>

<template>
  <div class="movies-container">
    <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie" />
  </div>
</template>

<style>
.movies-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
</style>
