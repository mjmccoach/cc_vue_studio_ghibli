<template>
  <article>
      <div>
            <h1> {{ movie.title }} </h1>
            <dl>
            <dt>Director :</dt>
            <dd> {{movie.director}} </dd>
            <dt>Release: </dt>
            <dd>{{ movie.release_date}} </dd>
            <dt>Description :</dt>
            <dd>{{ movie.description }}</dd>

            </dl>

      </div>

      <!-- <div class='characters'>
          <h2> {{ movie.title }}'s characters: </h2>
          <ul>
              <li
              v-for="(people,index) in movie.people"
              :key="index">
             {{ people.name }}
             </li>
          </ul>
      </div> -->
  </article>
</template>

<script>
export default {
    name :'movie-detail',
    props: ['movie'],
    // methods: {
    //     addFavourite: function() {
    //         eventBus.$emit("favourite-added", this.movie);
    //     }
    // }
};
</script>

<style>

article {
    display:grid;
}

</style>