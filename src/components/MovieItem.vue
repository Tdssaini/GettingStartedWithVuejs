<script setup>
const props = defineProps({
  movie: { type: Object, default: null },
  index: { type: Number, default: null },
});

const emit = defineEmits(["bookticket"]);

function bookTicket(){
  emit("bookticket", props.movie.id);
}

</script>

<template>
  <div class="movie-item">
    <div class="movie-item-image-wrapper">
      <img
        v-if="movie?.image"
        :src="movie.image"
        class="movie-item-image"
        :alt="movie.name"
      />
      <span v-else class="movie-item-no-image">
        <span class="text-4xl text-white">No image</span>
      </span>
    </div>

    <div >
      <div >
        <h3 >{{ movie.name }}</h3>
        <div class="movie-item-genres-wrapper">
          <span
            v-for="genre in movie.genres"
            :key="`${movie.id}-${genre}`"
            class="movie-item-genre-tag"
            >{{ genre }}</span
          >
        </div>
      </div>
      <div class="movie-item-description-wrapper">
        <p class="movie-item-description">{{ movie.description }}</p>
      </div>
      <div class="movie-item-rating-wrapper">
        <span class="movie-item-rating-text">
          Rating: ({{ movie.rating }}/5)
        </span>
      </div>
    </div>
    <button class="greenButton" @click="bookTicket">Book Tickets</button>
  </div>
</template>
<style scoped>
    .greenButton{
      color:white;
      background: green;
      padding:5px;
      margin-top:20px;
    }
</style>
