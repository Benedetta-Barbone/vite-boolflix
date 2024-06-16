
<script>
export default {
  name: 'MovieCard',
  props: {
    movie: {
      type: Object,
      required: true
    }
  }
}
</script>

<template>
  <div class="movie-card">
    <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" alt="Movie Poster" class="movie-poster">
    <div class="movie-details">
      <h2>{{ movie.title }}</h2>
      <p>{{ movie.overview }}</p>
    </div>
  </div>
</template>
<style scoped>
.movie-card {
  border: 1px solid #ddd;
  border-radius: 5px;
  overflow: hidden;
  margin: 10px;
  width: 200px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
.movie-poster {
  width: 100%;
  height: auto;
}
.movie-details {
  padding: 10px;
}
.movie-details h2 {
  font-size: 1.2em;
  margin: 10px 0;
}
.movie-details p {
  margin: 5px 0;
  color: #555;
}
</style>
