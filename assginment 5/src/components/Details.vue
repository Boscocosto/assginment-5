<script setup>
import axios from "axios";
import { onMounted } from 'vue';
import { useRoute } from "vue-router";

const route = useRoute();
const response = await axios.get(`https://api.themoviedb.org/3/movie/${route.params.id}?api_key=${import.meta.env.VITE_API_KEY}&append_to_response=videos`);
console.log(response.data);

onMounted(async () => {
  response.value = await axios.get(`https://api.themoviedb.org/3/movie/${route.params.id}?api_key=${import.meta.env.VITE_API_KEY}&append_to_response=videos`);
})
</script>

<template>
  <div class="movie-detail">
    <h1 class="movie-title">{{ response.data.original_title }}</h1>
    <img :src="`https://image.tmdb.org/t/p/w500${response.data.poster_path}`" alt="Movie Poster" class="movie-poster" />
    <p class="movie-overview">{{ response.data.overview }}</p>
    <p class="movie-release-date">Release Date: {{ response.data.release_date }}</p>
    <a class="movie-site" :href="response.data.homepage" target="_blank">Official Movie Site</a>
    <p class="movie-runtime">Runtime: {{ response.data.runtime }} minutes</p>
    <p class="movie-rating">Rating: {{ response.data.vote_average }} / 10</p>

    <h2 class="trailers-title">Trailers</h2>
    <div class="trailers-container">
      <div v-for="trailer in response.data.videos.results" :key="trailer.id" class="trailer-tile">
        <a :href="`https://www.youtube.com/watch?v=${trailer.key}`" target="_blank">
          <img :src="`https://img.youtube.com/vi/${trailer.key}/hqdefault.jpg`" alt="Trailer"
            class="trailer-thumbnail" />
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.movie-detail {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  min-height: 100vh;
  padding: 40px;
  border-radius: 8px;
  background-image: url('/popcorn.jpg');
  background-size: cover;
  background-position: center;
}

.movie-title {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 30px;
  text-align: center;
  color: #333;
}

.movie-poster {
  width: 100%;
  max-width: 400px;
  height: auto;
  border-radius: 8px;
  margin-bottom: 30px;
}

.movie-overview {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 30px;
  color: #000000;
  text-align: center;
}

.movie-release-date {
  font-size: 1.1rem;
  margin-bottom: 30px;
  color: #777;
}

.movie-site {
  display: inline-block;
  margin-bottom: 30px;
  padding: 12px 20px;
  background-color: #000000;
  color: white;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s;
}

.movie-site:hover {
  background-color: #2f2f2f;
}

.trailers-title {
  font-size: 2rem;
  margin: 30px 0;
  text-align: center;
  color: #000000;
}

.trailers-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.trailer-tile {
  max-width: 280px;
  width: 100%;
  border-radius: 8px;
}

.trailer-thumbnail {
  width: 100%;
  height: auto;
  border-radius: 8px;
}
</style>