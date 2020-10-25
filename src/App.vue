<template>
  
  <main>    
    <movie-list :movies='movies'></movie-list>
    <movie-detail v-if="selectedMovie" :movie='selectedMovie'></movie-detail>
    <favourite-list class='favourite-list' :favourites="favourites"></favourite-list>

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
      const promises = [1].map(num => {
        return fetch('https://ghibliapi.herokuapp.com/films')
          .then(response => response.json());
          // .then(movies => this.movies = movies);
      });


    Promise.all(promises)
      .then(movies => {
        const movieData = movies.reduce(
         (flat, toFlatten) => flat.concat(toFlatten),
         []
        );
        movieData.forEach(movie => (movie.isFavourite = false));
        this.movies = movieData;
      });
    },

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
    // fetch('https://ghibliapi.herokuapp.com/films')
    // .then(response => response.json())
    // .then(movies => this.movies = movies);
    this.getMovies();

    fetch('https://ghibliapi.herokuapp.com/people')
    .then(response => response.json())
    .then(characters => this.people = characters);

    eventBus.$on('movie-selected', (movie) => {
        this.selectedMovie = movie;
    });

    eventBus.$on('favourite-added', (movie) => this.markFavourite(movie));

    eventBus.$on('favourite-removed', (movie) => this.unmarkFavourite(movie));


  },


};

</script>

<style scoped>

main {
  display: grid;
  height: 100vh;
  grid-template-columns: 35fr 65fr;
  background: url('https://studioghiblimovies.com/wp-content/uploads/2020/03/barcode-scanners-qr-code-2d-code-creative-barcode.jpg');
  background-size:cover;
  color: whitesmoke;
  text-emphasis-color: goldenrod;
  text-shadow: black;
  font-family: 'Roboto', sans-serif;
}
ul {
  list-style-type: none;
  cursor: pointer;
  margin-right: 10px;
}


</style>
