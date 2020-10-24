<template>
  <main>
    <movie-list :movies='movies'></movie-list>
    <movie-detail v-if="selectedMovie" :movie='selectedMovie'></movie-detail>
    <favourite-list></favourite-list>

  </main>
</template>

<script>
import movieList from '@/components/movieList'
import movieListItem from '@/components/movieListItem'
import movieDetail from '@/components/movieDetails'
import favouriteList from '@/components/favouriteList'
import { eventBus } from '@/main.js'

export default {
  data() {
    return {
      movies : [],
      people: [],
      selectedMovie : null,
    };
  },

  components: {
    movieList,
    movieListItem,
    movieDetail,
    favouriteList
    
  },

  methods: {
    
    getMovies : function() {
      const promises = 

    },

    Promise.all(promises)
      .then(movies => {
        const movieData = movies.reduce(
         (flat, toFlatten) => flat.concat(toFlatten),
         []
        );
        movieData.forEach(movie => (movie.isFavourite = false));
        this.movies = movieData;
      })
    markFavourite : function(movie) {
      const index = this.movies.indexOf(movie);
      this.movies[index].isFavourite = true;
    },
    
    unmarkFavourite: function(movie) {
      const index = this.movies.indexOf(movie);
      this.movies[index].isFavourite = false;
    },


  },

  computed: {
    favourites: function () {
      return this.movies.filter(movie => movie.isFavourite);
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(movies => this.movies = movies);

    fetch('https://ghibliapi.herokuapp.com/people')
    .then(response => response.json())
    .then(characters => this.people = characters);

    eventBus.$on('movie-selected', (movie) => {
        this.selectedMovie = movie;
    });

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
