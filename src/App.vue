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
      // api key che ci servirà per le varie chiamate
      api_key:'4de8e24617b012aa2d57ca4c9f87b4d5'
    };
  },
  methods: {
    // qui effettuerò chiamata axios di theMovieDatabase Movie/search Api
    // quando chiamerò il metodo con search, inputKeyword avrà il valore della keyword presente nella sezione Headerbox/input
    // dichiaro una variabile params "parametri" a cui assegno come query dell'api la keyword
    // come api_key assegno valore salvato nei data
    // e facoltativamente  il linguaggio in italiano .in questo caso 'it'
    // la chiamata axios avrà parte dell'url base + i parametri assegnati
    // in questo caso l'array in data movie riceverà dati di result dall'Api
    movieSearch(inputKeyword) {
      const params = {
        query:inputKeyword,
        api_key:this.api_key,
        language:'it'
      }
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie`,{params}
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
