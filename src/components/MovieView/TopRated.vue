<template>

  <Head title="Top Rated" />
  <div class="slider-container">
    <div class="slider" ref="slider">
      <div v-for="movie in popularMovies">
        <MovieCard
          :title="movie.title"
          :image="movie.image"
          :score="movie.rank"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import MovieCard from './MovieCard.vue';
import Head from './Head.vue';
const popularMovies = ref([]);

onMounted(() => {
  fetch('datas/toprated.json')
    .then(response => response.json())
    .then(data => {
      popularMovies.value = data.popular;
    })
    .catch(error => console.error('Erreur lors du chargement du JSON:', error));
});
</script>

<style scoped>




  .slider-container {
    padding: 0 16px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .slider {
    display: flex;
    flex-wrap: nowrap;
    gap: 16px;
    padding: 0; 
    overflow-x: auto;
    scroll-behavior: smooth;
    margin: 0; 
  }
</style>