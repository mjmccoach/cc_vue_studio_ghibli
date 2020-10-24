<template>
  <main>
    <movie-list :movies='movies'></movie-list>
    <movie-detail v-if="selectedMovie" :movie='selectedMovie'></movie-detail>

  </main>
</template>

<script>
import movieList from '@/components/movieList'
import movieListItem from '@/components/movieListItem'
import movieDetail from '@/components/movieDetails'
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

    eventBus.$on('movie-selected', (movie) => {
        this.selectedMovie = movie;
    });

  },
  components: {
    movieList,
    movieListItem,
    movieDetail,
  },


};

</script>

<style scoped>

main {
  display: grid;
  height: 100vh;
  grid-template-columns: 35fr 65fr;
}
ul {
  list-style-type: none;
  cursor: pointer;
}


</style>
