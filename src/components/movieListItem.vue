<template>
  <li @click="handleClick">
    
    <span> {{ movie.title }} </span> ,
    <span> {{ movie.release_date}} </span>
      
  </li>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
    name: 'movie-list-item',
    props : ['movie'],
    methods: {
        handleClick: function (event) {
            eventBus.$emit("movie-selected", this.movie);   
        },
    },

}
</script>

<style>

</style>