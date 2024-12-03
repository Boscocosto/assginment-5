<script setup>
import Header from '../components/Header.vue';
import Hero from '../components/Hero.vue';
import Footer from '../components/Footer.vue';
import Feature from '../components/Feature.vue';
</script>

<template>
  <Header />  
  <div class="homePage">
    <Hero />
    <Feature />
  </div>
  <Footer />
</template>

<style scoped>
.homePage {
    background-image: url('/popcorn.jpg');
    background-size: cover;
    background-position: center;
    color: black;
    text-align: center;
    padding: 100px 20px;
    height: 100vh; /* Ensures the hero section takes up the entire viewport height */
    display: flex;
    flex-direction: column;
    justify-content: center; /* Vertically centers the content */
    align-items: center; /* Horizontally centers the content */
}
</style>