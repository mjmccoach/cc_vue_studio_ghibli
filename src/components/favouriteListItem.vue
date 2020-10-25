<template>
   <li>

       <span>{{ favourite.title }} </span>
       <span>{{ favourite.director }}</span>
       <span>{{ favourite.release_date}} </span>
   </li>
</template>

<script>
export default {
    name : "favourite-list-item",
    props: ['favourite']
}
</script>

<style>

</style>