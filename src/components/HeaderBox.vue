<template>
  <header>
    <!-- header strutturato con un logo del programma  -->
    <div class="logo">Boolflix</div>
    <ul>
      <!-- al click del tasto home il padre app svolgerà la funzione relativa-->
      <li @click="$emit('home')">Home</li>
      <li>Serie Tv</li>
      <li>Film</li>
      <li>Originali</li>
      <li>Aggiunti di Recente</li>
      <li>La mia lista</li>
    </ul>
    <!-- una user input con un input text e un bottone -->
    <div class="userInput">
      <!-- quando scrivo modificherò variabile keyword o parola chiave -->
      <input type="text" placeholder="Scrivi qui" v-model="keyword" />
      <!-- al click verrà ascoltato dal padre App tramite search che dovrà chiamare un metodo  -->
      <button @click="$emit('search', keyword)">Invia</button>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      // creo una variabile che legge il testo che scriverò sull'input
      keyword: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables.scss";
header {
  height: 60px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  background-color: $header-color;
  align-items: center;
  padding: 0 100px;
  .logo {
    color: $main-color;
    font-size: 30px;
  }
  ul {
    display: flex;
    list-style: none;
    li {
      color: $secondary-color;
      padding: 0px 10px;
      cursor: pointer;
      &:hover {
        color: $main-color;
      }
    }
  }
  .userInput {
    input {
      width: 200px;
      font-size: 15px;
    }
    button {
      background-color: $main-color;
      color: $secondary-color;
      padding: 5px 20px;
      border-radius: 5px;
      border: 2px solid $secondary-color;
      cursor: pointer;
    }
  }
}
</style>