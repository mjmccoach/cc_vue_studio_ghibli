<template>
   <li>

       <span>{{ movie.title }} </span>
       <span>{{ movie.director }}</span>
       <span>{{ movie.release_date}} </span>
       <button class="delete-button" v-on:click="removeFavourite">Remove Favourite</button>
   </li>
</template>

<script>

import { eventBus } from '@/main.js';

export default {
    name : "favourite-list-item",
    props: ['movie'],
    methods : {
        removeFavourite : function(event) {
            eventBus.$emit('favourite-removed', this.movie)
        }
    }
}
</script>

<style>
    .delete-button:hover{
        background-color: red;
        cursor: pointer;
    }
</style>