<template>
  
  <ul>
  <movie-list-item 
  v-for="(movie,index) in movies"
  :key="index"
  :movie="movie">
  </movie-list-item>
  </ul>

</template>

<script>

import movieListItem from '@/components/movieListItem'

export default {
    name :'movie-list',
    components : {
        movieListItem,
    },
    props: ['movies'],
};
</script>

<style>

</style>