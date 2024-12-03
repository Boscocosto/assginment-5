<script setup>
import axios from "axios";
import { ref, onMounted } from 'vue';
import { useRouter } from "vue-router";

const props = defineProps(["genres"]);
const router = useRouter();
const selectedGenre = ref(28);
const response = ref(null);

const genres = [
  { id: 12, genreName: 'Adventure' },
  { id: 16, genreName: 'Animation' },
  { id: 35, genreName: 'Comedy' },
  { id: 10402, genreName: 'Music' },
  { id: 878, genreName: 'Sci-Fi' },
];

async function getMovieByGenre() {
  response.value = await axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=${import.meta.env.VITE_API_KEY}&include_adult=false&with_genres=${selectedGenre.value}`);
}

function getMovieDetails(id) {
  router.push(`/movies/${id}`)
}

onMounted(async () => {
  response.value = await axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=${import.meta.env.VITE_API_KEY}&include_adult=false&with_genres=${selectedGenre.value}`);
})
</script>

<template>
  <div class="movie-gallery">
    <select v-model="selectedGenre" @change="getMovieByGenre()">
      <option v-for="genre of genres" :value="genre.id">{{ genre.genreName }}</option>
    </select>
    <div v-if="response" class="movie-list">
      <div v-for="movie in response.data.results" :key="movie.id" class="movie-card" @click="getMovieDetails(movie.id)">
        <img :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`" alt="Movie Poster" class="movie-poster" />
        <p class="movie-title">{{ movie.title }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Movie Gallery Container */
.movie-gallery {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  background-color: #f4f4f4;
  /* Light background for the whole gallery */
  min-height: 100vh;
}

/* Genre Selection Dropdown */
select {
  padding: 12px;
  font-size: 16px;
  border: 2px solid #ccc;
  border-radius: 5px;
  width: 250px;
  cursor: pointer;
  background-color: #fff;
  transition: border-color 0.3s ease;
}

select:focus {
  border-color: #007bff;
  /* Highlighted border on focus */
}

/* Movie List Container */
.movie-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  /* Flexible grid */
  gap: 20px;
  width: 100%;
  max-width: 1200px;
  /* Max width for better alignment */
  margin-top: 20px;
  padding: 0 20px;
}

/* Individual Movie Card */
.movie-card {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.movie-card:hover {
  transform: scale(1.05);
  /* Zoom effect on hover */
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  /* Enhanced shadow */
}

/* Movie Poster Image */
.movie-poster {
  width: 100%;
  height: 300px;
  /* Set a fixed height for uniformity */
  object-fit: cover;
  /* Ensure images cover the area without distortion */
  border-bottom: 3px solid #f4f4f4;
  /* Optional border between the image and title */
}

/* Movie Title */
.movie-title {
  font-size: 18px;
  text-align: center;
  padding: 15px;
  font-weight: bold;
  color: #333;
  background-color: #f9f9f9;
  margin: 0;
  border-top: 1px solid #ccc;
}

/* Responsive Design */
@media (max-width: 768px) {
  .movie-gallery {
    padding: 10px;
  }

  .select {
    width: 200px;
  }

  .movie-list {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    /* Adjust for smaller screens */
  }
}
</style>