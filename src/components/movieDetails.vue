<template>
  <article>
      <h1> {{ movie.title }} </h1>
      <dl>
          


      </dl>
  </article>
</template>

<script>
export default {
    name :'movie-detail',
    props: ['movie'],
};
</script>

<style>

article {
    display:grid;
}

</style>