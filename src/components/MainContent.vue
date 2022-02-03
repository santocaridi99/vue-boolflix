<template>
    <div class="container">
        <!-- nel container avrò che per ogni oggetto  movie presente in  movies , con chiave l'id avrò una card -->
       <div v-for="movie in movies" :key="movie.id" class="card">
           <!-- all'img do con il template literal parte del link preso dal file condiviso + il valore relativo all'immagine -->
           <!-- ad alt do il titolo del film -->
           <img :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`" :alt="movie.title">
           <!-- la text area sarà visibile solo in  hover -->
           <!-- avrà i vari valori dell'oggetto movie -->
           <div class="textArea">
               <p><strong>Titolo:</strong> <span>{{movie.title}}</span></p>
               <p><strong>Titolo originale:</strong> <span>{{movie.original_title}}</span></p>
               <p>
                   <strong>Lingua:</strong>
                   <span>{{movie.original_language}}
                       <!-- se nell'array di lingue è inclusa quella ricevuta dall'api allora mostra la bandiera -->
                       <img v-if="originalLanguage.includes(movie.original_language)" :src="`/flags/${movie.original_language}.png`" :alt="movie.original_language">
                       <!-- altrimenti mostra un placeholder -->
                       <img v-else src="https://via.placeholder.com/12" alt="dummy">
                   </span>
                </p>
               <p><strong>Voto: </strong><span>{{movie.popularity}}</span></p>
               <p><strong>Overview: </strong><span>{{movie.overview}}</span></p>
           </div>
       </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            // array di lingue presenti
            originalLanguage:['de','en','es','fr','it']
        }
    },
    props:{
        // movies è un Array
        movies:Array,
    },
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
        height: 350px;
        background-color: gray;
        border: 2px solid white;
        position: relative;
        // hover di card in text area che lo trasformerà da display none in display block
        &:hover .textArea{
            display: block;
        }
        img{
            width: 100%;
            height: 100%;
        }
        .textArea{
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
            p{
                margin-top: 4px;
                span{
                    img{
                        width: 12px;
                        height: 12px;
                    }
                }
            }
        }
    }
}
</style>