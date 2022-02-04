<template>
  <div class="container">
    <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
    <!-- card nel card container corrisponde al movie oggetti in movies -->
    <card-container v-for="movie in movies" :key="movie.id" :card="movie">
    </card-container>
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
</style>