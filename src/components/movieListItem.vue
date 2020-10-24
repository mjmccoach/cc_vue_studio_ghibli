<template>
  <li>
    
    <span> {{ movie.title }} </span> ,
    <span> {{ movie.release_date}} </span>
      
  </li>
</template>

<script>
export default {
    name: 'movie-list-item',
    props : ['movie'],

}
</script>

<style>

</style>