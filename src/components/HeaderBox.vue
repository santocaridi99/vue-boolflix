<template>
  <header>
      <!-- header strutturato con un logo del programma  -->
    <div class="logo">Boolflix</div>
    <!-- una user input con un input text e un bottone -->
    <div class="userInput">
        <!-- quando scrivo modificherò variabile keyword o parola chiave -->
      <input type="text" placeholder="Scrivi qui" v-model="keyword" />
      <!-- al click verrà ascoltato dal padre App tramite search che dovrà chiamare un metodo  -->
      <button @click="$emit('search',keyword)">Invia</button>
    </div>
  </header>
</template>

<script>
export default {
    data(){
        return{
            // creo una variabile che legge il testo che scriverò sull'input
            keyword:'',
        }
    }
};
</script>

<style lang="scss" scoped>
header {
  height: 60px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  background-color: #191919;
  align-items: center;
  padding: 0 100px;
  .logo {
    color: red;
    font-size: 25px;
  }
}
</style>