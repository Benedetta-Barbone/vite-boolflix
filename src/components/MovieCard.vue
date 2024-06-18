<script>
export default {
  name: 'MovieCard',
  props: {
    movie: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      hover: false
    };
  },
  computed: {
    movieStars() {
      return Math.ceil(this.movie.vote_average / 2);
    }
  },
  methods: {
    getFlagClass(languageCode) {
      const langToCountry = {
        en: 'us',
        it: 'it',
        fr: 'fr',
        es: 'es',
        de: 'de',
        ja: 'jp',
      };
      return langToCountry[languageCode] || 'unknown';
    },
    getFullImagePath(posterPath) {
      const baseUrl = 'https://image.tmdb.org/t/p/';
      const size = 'w200';
      return `${baseUrl}${size}${posterPath}`;
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
      <p>Lingua: <span :class="`fi fi-${getFlagClass(movie.original_language)}`"></span></p>
      <p>
        Voto: 
        <span v-for="star in 5" :key="star">
          <font-awesome-icon :icon="star <= movieStars ? 'star' : ['far', 'star']" />
        </span>
      </p>
    </div>
  </div>
</template>


<style scoped>
@import 'flag-icons/css/flag-icons.min.css';

.movie-card {
  position: relative;
  width: 300px;
  height: 450px;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s;
}
.movie-card:hover {
  transform: scale(1.05);
}
.movie-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.movie-details {
  position: absolute;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  width: 100%;
  padding: 10px;
  opacity: 0;
  transition: opacity 0.3s;
}
.movie-card:hover .movie-details {
  opacity: 1;
}
.movie-details h2,
.movie-details h3 {
  margin: 0;
  padding: 0;
}
.movie-details p {
  margin: 10px 0;
}
</style>
