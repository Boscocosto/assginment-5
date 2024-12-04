<script setup>
import Genres from "../components/Genres.vue";
import Header from "../components/Header.vue"
import Footer from "../components/Footer.vue"

const genres = [
  { id: 12, genreName: 'Adventure' },
  { id: 53, genreName: 'Thriller' },
  { id: 16, genreName: 'Animation' },
  { id: 9648, genreName: 'Mystery' },
  { id: 27, genreName: 'Horror' },
  { id: 28, genreName: 'Action' },
];
</script>

<template>
  <Header />
  <Genres :genres="genresList" />
  <Footer />
</template>

<style scoped></style>