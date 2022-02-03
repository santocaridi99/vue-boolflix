<template>
  <header>
    <div class="logo">Boolflix</div>
    <div class="userInput">
      <input type="text" placeholder="Scrivi qui" />
      <button>Invia</button>
    </div>
  </header>
</template>

<script>
export default {};
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