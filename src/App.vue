<template>
  <main>
    <movie-list :movies='movies'></movie-list>

  </main>
</template>

<script>
import movieList from '@/components/movieList'
import movieListItem from '@/components/movieListItem'

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
