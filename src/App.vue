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
      characters: [],
      selectedMovie : null,
    };
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(movies => this.movies = movies);

    fetch('https://ghibliapi.herokuapp.com/people')
    .then(response => response.json())
    .then(characters => this.characters = characters);

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
  background: url('https://i.redd.it/w6pf76e6p0v51.jpg') opacity 90%;
  background-size: contain;
  color: goldenrod;
  text-emphasis-color: goldenrod;
  text-shadow: black;
}
ul {
  list-style-type: none;
  cursor: pointer;
}


</style>
