<template>
    <div class="container">
       <div v-for="movie in movies" :key="movie.id" class="card">
           <img :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`" alt="">
       </div>
    </div>
</template>

<script>
export default {
    props:{
        movies:Object,
    }
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
        img{
            width: 100%;
            height: 100%;
        }
    }
}
</style>