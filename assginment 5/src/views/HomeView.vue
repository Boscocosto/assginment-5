<script setup>
import Header from '../components/Header.vue';
import Hero from '../components/Hero.vue';
import Footer from '../components/Footer.vue';
import Feature from '../components/Feature.vue';
</script>

<template>
    <Header />
    <Hero />
    <Feature/>
    <Footer />
</template>

<style scoped>
body {
    background-image: url('popcorn.jpg');
    background-size: cover;
    background-position: center top;
    margin: 0;
}
</style>