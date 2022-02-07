<template>
  <div class="card">
    <!-- all'img do con il template literal parte del link preso dal file condiviso + il valore relativo all'immagine -->
    <!-- ad alt do il titolo del film -->
    <img
      :src="`https://image.tmdb.org/t/p/original${card.poster_path}`"
      :alt="title"
    />
    <!-- la text area sarà visibile solo in  hover -->
    <!-- avrà i vari valori dell'oggetto movie -->
    <div class="textArea">
      <p>
        <strong>Titolo:</strong> <span>{{ title }}</span>
      </p>
      <p>
        <strong>Titolo originale:</strong>
        <span>{{ originalTitle }}</span>
      </p>
      <p>
        <strong>Lingua:</strong>
        <span
          >{{ card.original_language }}
          <!-- se nell'array di lingue è inclusa quella ricevuta dall'api allora mostra la bandiera -->
          <img
            v-if="originalLanguage.includes(card.original_language)"
            :src="`/flags/${card.original_language}.png`"
            :alt="card.original_language"
          />
          <!-- altrimenti mostra un placeholder -->
          <img v-else src="https://via.placeholder.com/12" alt="dummy" />
        </span>
      </p>
      <p>
        <strong>Voto: </strong>
        <!-- avrò una stellina per ogni voto che è decimale da 1 a 10 che dividendo per due diventerà ( un numero da 1 a 5) -->
        <!-- uso mathround per calcolare per eccesso o difetto -->
        <stars-rating :average="card.vote_average"></stars-rating>
      </p>
      <p>
        <strong>Overview: </strong><span>{{ card.overview }}</span>
      </p>
      <p>
        <strong>Cast:</strong>
        <!-- faccio un for per tutte le persone che ci sono nel cast -->
        <!-- se indice è minore di 5 stampo il nome -->
        <span v-for="(people , i) in cast" :key="i">
          <span v-if="i<=5">{{people.name}}.</span>
        </span>
      </p>
      <p>
        <strong>Generi:</strong><span>{{card.genre_ids}}</span>
      </p>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import StarsRating from "./StarsRating.vue";
export default {
  components: {
    StarsRating,
  },
  props: {
    //   card sarà un oggetto
    card: Object,
    // passo anche title come stringa
    title: String,
    // passo originaltitle come stringa
    originalTitle: String,
    // passo id
    contentId:Number,
    // passo tipo 
    type:String
  },
  data() {
    return {
      // array di lingue presenti
      originalLanguage: ["de", "en", "es", "fr", "it"],
      // array del cast
      cast:[],
    };
  },
  methods:{
    // metodo per prendere api cast
    async getCast(){
      this.cast=await this.castApi()
    },
    async castApi(){
      const result = await axios.get(`https://api.themoviedb.org/3/${this.type}/${this.contentId}/credits?api_key=4de8e24617b012aa2d57ca4c9f87b4d5&language=it`).then((res)=>{
        return res.data.cast;
      });
      return result;
    }
  },
  // lo chiamo con mounted
  mounted(){
    this.getCast();
  }
};
</script>
<style lang="scss" scoped>
@import "../style/cardstyle.scss";
</style>