<template>
  <li @click="handleClick">
    
    <span> {{ movie.title }} </span> ,
    <span> {{ movie.release_date}} </span>
    <button v-if="!movie.isFavourite" v-on:click="addFavourite">Add Favourite</button>
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

        addFavourite: function (event) {
            eventBus.$emit("favourite-added", this.movie)
        }

    },

}
</script>

<style>

</style>