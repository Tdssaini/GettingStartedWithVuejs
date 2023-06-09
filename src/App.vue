<script setup>
import { ref } from 'vue';
import MovieItem from "./components/MovieItem.vue";
import { items } from "./assets/movies.json";
import axios from 'axios'

const movies = ref(items);

function bookTicket(id) {
  axios
      .get('https://mocki.io/v1/a96e319c-d49d-433f-8c86-231bd1e39067?movieid='+id)
      .then((response) => {
          alert('Your ticket booking status is '+response.data.booked);
      })
}
</script>

<template>
  <div class="app">
    <div class="movie-list">
        <MovieItem
          v-for="movie in movies"
          :key="movie.id"
          :movie="movie"
          @bookticket="bookTicket"
        />
      </div>
  </div>
</template>
