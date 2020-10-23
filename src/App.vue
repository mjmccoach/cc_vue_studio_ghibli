<template>
  <h1>Bob's your uncle</h1>
</template>

<script>
export default {
  data() {
    return {
      movies : [],
    };
  };
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())

  }

}
</script>

<style>

</style>
