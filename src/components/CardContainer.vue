<template>
  <div class="card">
    <!-- all'img do con il template literal parte del link preso dal file condiviso + il valore relativo all'immagine -->
    <!-- ad alt do il titolo del film -->
    <img
      :src="`https://image.tmdb.org/t/p/original${card.poster_path}`"
      :alt="card.title"
    />
    <!-- la text area sarà visibile solo in  hover -->
    <!-- avrà i vari valori dell'oggetto movie -->
    <div class="textArea">
      <p>
        <strong>Titolo:</strong> <span>{{ card.title }}</span>
      </p>
      <p>
        <strong>Titolo originale:</strong>
        <span>{{ card.original_title }}</span>
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
        <strong>Voto: </strong><span>{{ card.popularity }}</span>
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
.card {
  width: calc(100% / 4 - 60px);
  margin: 60px;
  height: 350px;
  background-color: gray;
  border: 2px solid white;
  position: relative;
  // hover di card in text area che lo trasformerà da display none in display block
  &:hover .textArea {
    display: block;
  }
  img {
    width: 100%;
    height: 100%;
  }
  .textArea {
    color: white;
    width: 100%;
    height: 100%;
    position: absolute;
    display: none;
    top: 0;
    left: 0;
    display: none;
    background-color: gray;
    font-size: 12px;
    padding: 5px;
    overflow-y: auto;
    p {
      margin-top: 4px;
      span {
        img {
          width: 12px;
          height: 12px;
        }
      }
    }
  }
}
</style>