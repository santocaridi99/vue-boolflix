<template>
  <div id="app">
    <!-- search nella sezione Headerbox input chiamerà metodo movieSearch -->
    <header-box @search='movieSearch'></header-box>
    <!-- movies nel maincontent corrisponde all'array movies in app -->
    <main-content :movies="movies"></main-content>
  </div>
</template>

<script>
// importo axios
import axios from "axios";
// importo headerbox
import HeaderBox from "./components/HeaderBox.vue";
// importo maincontent
import MainContent from "./components/MainContent.vue";
export default {
  name: "App",
  components: {
    HeaderBox,
    MainContent,
  },
  data() {
    return {
      // creo un array vuoto di film
      movies: [],
    };
  },
  methods: {
    // qui effettuerò chiamata axios di theMovieDatabase Movie/search Api
    // uso il template literal su get e do alla query un valore inputkeyword
    // che quando chiamerò il metodo con search avrà il valore della keyword presente nella sezione Headerbox/input
    // array movies corrisponderà al response data dell'api
    movieSearch(inputKeyword) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=4de8e24617b012aa2d57ca4c9f87b4d5&language=it&query=${inputKeyword}&page=1&include_adult=false`
        )
        .then((response) => {
          this.movies=response.data.results
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
