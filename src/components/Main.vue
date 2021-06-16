<template>
    <div class="container">
        
        <h2 v-if="search" class="categoria">Film:</h2>
        <div class="film" v-for="(movie, index) in movies" :key="movie.id">
            <h2>{{ movie.title }}</h2>
            <h2>{{ movie.original_title }}</h2>
            <img 
            :src="finalUrlMovie(index)" 
            v-if="finalUrlMovie(index) != null"
            alt="Copertina Film" class="copertina">
            <img 
            v-else
            src="../assets/images/anteprima.png" alt="">
            <img 
              class="bandiera"
              v-if="movie.original_language=='it' "
              src="../assets/images/it.png" 
              alt="bandiera italiana">
            <img 
              class="bandiera"
              v-else-if="movie.original_language=='en'" 
              src="../assets/images/en.png" 
              alt="bandiera inglese">
            <h2 v-else>{{ movie.original_language }}</h2>
            <div class="ratings">
                <i 
                    v-for="i in 10" :key="i" 
                    :class="(intero(movie.vote_average) > i) ? 'fas' : 'far'"
                    class="fa-star"
                ></i>
            </div>
            <div class="overlay"></div>
        </div>
        <h2 v-if="search" class="categoria">Serie TV:</h2>
        <div class="serie" v-for="(serie, index) in series" :key="serie.id">
            <h2>{{ serie.name }}</h2>
            <h2>{{ serie.original_name }}</h2>
            <img 
            :src="finalUrlSeries(index)" 
            v-if="finalUrlSeries(index) != null"
            alt="Copertina Serie" class="copertina">
            <img 
            v-else
            src="../assets/images/anteprima.png" alt="">
            <img 
              class="bandiera"
              v-if="serie.original_language=='it' "
              src="../assets/images/it.png" 
              alt="bandiera italiana">
            <img
              class="bandiera"
              v-else-if="serie.original_language=='en'" 
              src="../assets/images/en.png" 
              alt="bandiera inglese">
            <h2 v-else>{{ serie.original_language }}</h2>
            <div class="ratings">
                <i
                v-for="i in 10" :key="i" 
                    :class="(intero(serie.vote_average) > i) ? 'fas' : 'far'"
                    class="fa-star"
                    ></i>
            </div>
            <div class="overlay"></div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Main',
    props: {
        movies: Array,
        series: Array,
        search: Boolean,
        // cover: Array
    },
    data() {
        return {
            baseURL: "https://image.tmdb.org/t/p/w342"
        }
    },
    methods: {
        finalUrlMovie: function(index) {
            if(this.movies[index].poster_path != null) {
                return this.finalSrc= `${this.baseURL}${this.movies[index].poster_path}`
            }
        },

        finalUrlSeries: function(index) {
            if (this.series[index].poster_path) {
                return this.finalSrc= `${this.baseURL}${this.series[index].poster_path}`
            }
        },
        intero: function(int) {
            // console.log(int);
            return Math.trunc(int);
        }
    },
        
}
</script>


<style lang="scss" scoped>
 @import '~@fortawesome/fontawesome-free/css/all.min.css';

    .container {
        display: flex;
        justify-content: flex-start;
        flex-wrap: wrap;
        overflow: auto;
        height: calc(100vh - 100px);
        background-color: #E94F02;
    }

    .categoria {

        width: 100%;
        padding-left: 10px;
    }

    .film, .serie {
        display: flex;
        position: relative;
        flex-direction: column;
        justify-content: space-around;
        width: 15%;
        height: 300px;
        margin: 20px;
        padding-left: 5px;
        font-size: 10px;
        color: white;
        overflow: hidden;

        * {
            position: relative;
            z-index: 2;
        }
        .bandiera {
            width: 25px;
        }
        .copertina {
            position: absolute;
            z-index: 1;
            width: 100%;
            
            &:hover {
                z-index: 1;
            }
        }
        .overlay {
            position: absolute;
            z-index: 1;
            height: 100%;
            width: 100%;
            background-color: rgba(0,0,0,0.5);
        }
        .copertina ~ .overlay:hover {
            z-index: 1;
        }
    }

</style>