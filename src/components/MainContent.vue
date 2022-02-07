<template>
  <div class="mainContainer">
    <div class="filmSection">
      <!-- scritta compare solo se array è pieno -->
      <!-- scritta è dinamica  -->
      <h1 v-if="movies.length > 0">{{ ftitle }}</h1>
      <!-- pulsante sinistro -->
      <div v-if="movies.length > 0" class="left">
        <i class="fas fa-chevron-circle-left"></i>
      </div>
      <div class="container">
        <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
        <!-- card nel card container corrisponde al movie oggetti in movies -->
        <!-- title nel card container corrisponderà a movie.title-->
        <!-- originalTitile ugualmente corrisponde a movie.original_title -->
        <!-- type è una stringa  -->
        <card-container
          v-for="movie in movies"
          :key="movie.id"
          :card="movie"
          :title="movie.title"
          :originalTitle="movie.original_title"
          :contentId="movie.id"
          :type="'movie'"
        >
        </card-container>
      </div>
      <div v-if="movies.length>0" class="right">
        <i class="fas fa-chevron-circle-right"></i>
      </div>
    </div>
    <div class="serieSection">
      <!-- scritta compare solo se array è pieno -->
      <!-- scritta dinamica -->
      <h1 v-if="series.length > 0">{{ stitle }}</h1>
      <div v-if="series.length> 0" class="left">
        <i class="fas fa-chevron-circle-left"></i>
      </div>
      <div class="container">
        <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
        <!-- card nel card container corrisponde al movie oggetti in movies -->
        <!-- title in questo caso corrisponde a serie.name essendo api diversa -->
        <!-- ugualmente originalTittle corrisponde a serie.original_name -->
        <!-- type è una stringa -->
        <card-container
          v-for="serie in series"
          :key="serie.id"
          :card="serie"
          :title="serie.name"
          :originalTitle="serie.original_name"
          :contentId="serie.id"
          :type="'tv'"
        >
        </card-container>
      </div>
      <!-- pulsante destro -->
      <div v-if="series.length>0" class="right">
        <i class="fas fa-chevron-circle-right"></i>
      </div>
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
    // passo le variabili dei titoli come stringhe
    stitle: String,
    ftitle: String,
  },
};
</script>
<style lang="scss" scoped>
@import "@/style/variables.scss";
// style
.mainContainer {
  padding: 10px;
  margin-top: 50px;
  .filmSection,
  .serieSection {
    position: relative;
    width: 100%;
    .container {
      width: 1200px;
      margin: 0 auto;
      margin-bottom: 10px;
      overflow-x: auto;
      overflow-y: hidden;
      display: flex;
    }
    h1 {
      margin-left: 150px;
      color: $secondary-color;
      margin-bottom: 5px;
    }
    .fas {
      font-size: 50px;
      color:$main-color;
      height: 100%;
    }
    .left {
      position: absolute;
      top: 50%;
      left: 5%;
      cursor: pointer;
    }
    .right {
      position: absolute;
      right: 5%;
      top: 50%;
      cursor: pointer;
    }
  }
}
</style>