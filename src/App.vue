<template>
  <main>
    <movie-list :movies='movies'></movie-list>

  </main>
</template>

<script>
import movieList from '@/components/movieList'
import movieListItem from '@/components/movieListItem'
import { eventBus } from '@/main.js'

export default {
  data() {
    return {
      movies : [],
      selectedMovie : null,
    };
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(movies => this.movies = movies);

    eventBus.$on('movie-selected', movie)

  },
  components: {
    movieList,
    movieListItem
  },


};

</script>

<style>

ul {
  list-style-type: none;
  cursor: pointer;
}

</style>
