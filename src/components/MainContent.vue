<template>
  <div class="mainContainer">
    <!-- scritta compare solo se array è pieno -->
    <h1 v-if="movies.length > 0">FILM</h1>
    <div class="container">
      <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
      <!-- card nel card container corrisponde al movie oggetti in movies -->
      <!-- title nel card container corrisponderà a movie.original_title -->
      <card-container
        v-for="movie in movies"
        :key="movie.id"
        :card="movie"
        :title="movie.original_title"
      >
      </card-container>
    </div>
    <!-- scritta compare solo se array è pieno -->
    <h1 v-if="series.length > 0">Serie Tv</h1>
    <div class="container">
      <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
      <!-- card nel card container corrisponde al movie oggetti in movies -->
      <!-- title in questo caso corrisponde a serie.name essendo api diversa -->
      <card-container
        v-for="serie in series"
        :key="serie.id"
        :card="serie"
        :title="serie.name"
      >
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
.mainContainer {
  width:1200px;
  margin: 0 auto;
  height: 100vh;
  .container {
    width: 1200px;
    margin-bottom: 50px;
    overflow-x: scroll;
    display: flex;
  }
  h1 {
    padding-left: 60px;
    color: red;
  }
}
</style>