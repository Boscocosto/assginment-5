<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div>
        <div class="header">
            <div class="logo">
                <img src="/src/assets/movie.png" class="logo"/>
                <h1>Pop Movies</h1>
            </div>
            <div class="buttons">
                <RouterLink to="/register" class="button register">Register</RouterLink>
                <RouterLink to="/login" class="button login">Login</RouterLink>
            </div>
        </div>    

        <div class="hero">
            <h1>Welcome to Pop Movies</h1>
            <p>A place where you can watch all your favorite movies for free in one place</p>
            <button type="button">Explore Now</button>
        </div>
    </div>
</template>

<style scoped>
body {
    background-image: url('popcorn.jpg');
    background-size: cover;
    background-position: center top;
    margin: 0;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1%;
    background-color: white;
    border: 2px solid rgba(0, 0, 0, 0.8);
    border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    margin: 20px;
}

.logo {
    display: flex;
    align-items: center;
}

.logo img {
    height: 50px;
    margin-right: 10px;
}

.buttons {
    display: flex;
    gap: 10px;
}

.button {
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #000000;
    color: white;
    transition: background-color 0.3s;
}

.button:hover {
    background-color: #0000008d;
}

.hero {
    background-image: url('hero-background.jpg');
    background-size: cover;
    background-position: center;
    color: black;
    text-align: center;
    padding: 100px 20px;
}

footer {
    text-align: center;
}
</style>