<template>
    <div class="container">
       <div class="card"></div>
       <div class="card"></div>
       <div class="card"></div>
       <div class="card"></div>
       <div class="card"></div>
       <div class="card"></div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.container{
    width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    .card{
        width: calc(100% / 4 - 60px);
        margin: 60px;
        height: 300px;
        background-color: gray;
        border: 2px solid white;
    }
}
</style>