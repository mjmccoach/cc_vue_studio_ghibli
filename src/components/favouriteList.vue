<template>
  <ul>
      <favourite-list-item
      v-for="(movie,index) in favourites"
      :key="index"
      :movie="movie"
      >
          
      </favourite-list-item>
  </ul>
</template>

<script>

import favouriteListItem from '@/components/favouriteListItem'

export default {
    name : 'favourite-list',
    components : {
        favouriteListItem,
    },
    props: ['favourites']
}
</script>

<style>

</style>