<template>
  <article>
      <h1> {{ movie.title }} </h1>
      <dl>
        <dt>Director :</dt>
        <dd> {{movie.director}} </dd>
        <dt>Release: </dt>
        <dd>{{ movie.release_date}} </dd>
        <dt>Description :</dt>
        <dd>{{ movie.description }}</dd>

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