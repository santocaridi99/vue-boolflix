<template>
  <div id="app">
    <!-- search nella sezione Headerbox input chiamerà metodo movieSearch -->
    <header-box @search="searchContent"></header-box>
    <!-- movies nel maincontent corrisponde all'array movies in app -->
    <!-- series corrisponde all'array series in app -->
    <main-content :movies="movies" :series="series"></main-content>
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
      // creo array per le serie tv
      series: [],
      // api key che ci servirà per le varie chiamate
      api_key: "4de8e24617b012aa2d57ca4c9f87b4d5",
    };
  },
  methods: {
    // step(2)
    // funzione searchContent o cerca di contenuti. accetta in ingresso la inputKeyword
    // che corrisponde alla keyword inserita nell'input in Headerbox
    // la funzione verrà usata nella  search o ricerca
    // questa funzione popola i due array (serie e film)
    // chiamando gli api con ingresso i relativi tipi e la keyword
    // si popoleranno aspettando "await" la chiamata api
    // quindi anche questa funzione sarà asincrona
    async searchContent(inputKeyword) {
      (this.movies = await this.movieDbApi("movie", inputKeyword)),
        (this.series = await this.movieDbApi("tv", inputKeyword));
    },
    // primo step(1) creo chiamata api
    // avrà type = il tipo (film o serie tv) che inseriremo nell url del get della chiamata
    // e inputKeyword che corrispondera alla keyword data dall'input nell header box
    // dichiaro una variabile params "parametri" a cui assegno come query dell'api la keyword
    // come api_key assegno valore salvato nei data
    // e facoltativamente  il linguaggio in italiano .in questo caso 'it'
    // la chiamata api con axios  la consegnamo ad una variabile result
    // prima di eseguire il return (inizialmente è un esecuzione sincrona )
    // aspetta con await ,una volta eseguita la chiamata ritorna result 
    // la chiamata api ,dopo ave inserito l'await dovrà essere preceduta con "async"
    // passo allo step(2)
    async movieDbApi(type, inputKeyword) {
      const params = {
        query: inputKeyword,
        api_key: this.api_key,
        language: "it",
      };
      const result = await axios
        .get(`https://api.themoviedb.org/3/search/${type}`, { params })
        .then((response) => {
          return response.data.results;
        });
      return result;
    },
  },
};
</script>

<style lang="scss">
// import main scss
@import "./style/main.scss";
// import fontawesome
// importo font awesome
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
</style>
