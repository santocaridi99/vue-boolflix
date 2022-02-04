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
        <span>{{ title }}</span>
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
        <i
          v-for="i in Math.round(card.vote_average / 2)"
          :key="i"
          class="fas fa-star"
        ></i>
      </p>
      <p>
        <strong>Overview: </strong><span>{{ card.overview }}</span>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    //   card sarà un oggetto
    card: Object,
    // passo anche title come stringa
    title: String,
  },
  data() {
    return {
      // array di lingue presenti
      originalLanguage: ["de", "en", "es", "fr", "it"],
    };
  },
};
</script>
<style lang="scss" scoped>
@import "../style/cardstyle.scss";
</style>