<template>
  <div id="app">
    <header-box></header-box>
    <main-content></main-content>
  </div>
</template>

<script>
// importo headerbox
import HeaderBox from './components/HeaderBox.vue'
// importo maincontent
import MainContent from './components/MainContent.vue'
export default {
  name: 'App',
  components: {
    HeaderBox,
    MainContent
  }
}
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
