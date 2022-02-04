<template>
  <div>
    <h3>FILM</h3>
    <div class="container">
      <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
      <!-- card nel card container corrisponde al movie oggetti in movies -->
      <!-- title nel card container corrisponderà a movie.original_title -->
      <card-container v-for="movie in movies" :key="movie.id" :card="movie" :title="movie.original_title">
      </card-container>
    </div>
    <h3>Serie Tv</h3>
    <div class="container">
      <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
      <!-- card nel card container corrisponde al movie oggetti in movies -->
      <!-- title in questo caso corrisponde a serie.name essendo api diversa -->
      <card-container v-for="serie in series" :key="serie.id" :card="serie" :title="serie.name">
      </card-container>
    </div>
  </div>
</template>

<script>
import CardContainer from "./CardContainer.vue";
export default {
  components: {
    //   componente card
    CardContainer,
  },
  props: {
    // movies è un Array
    movies: Array,
    series: Array,
  },
};
</script>
<style lang="scss" scoped>
// style
.container {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}
h3 {
  color: red;
}
</style>