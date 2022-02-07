<template>
  <!-- avrò una stellina per ogni voto che è decimale da 1 a 10 che dividendo per due diventerà ( un numero da 1 a 5) -->
  <!-- uso mathround per calcolare per eccesso o difetto -->
  <span>
    <i v-for="i in Math.round(average / 2)" :key="i" class="fas fa-star"></i>
  </span>
</template>
<script>
export default {
  props: {
    average: Number,
  },
};
</script>
<style lang="scss" scoped>
i {
  color: yellow;
}
</style>