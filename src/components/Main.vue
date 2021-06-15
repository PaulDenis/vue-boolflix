<template>
    <div>
        
        <div class="film" v-for="(movie, index) in movies" :key="index">
            <h2>Film</h2>
            <h2>{{ movie.title }}</h2>
            <h2>{{ movie.original_title }}</h2>
            <img 
              v-if="movie.original_language=='it' "
              src="../assets/images/it.png" 
              alt="bandiera italiana">
            <img
              v-else-if="movie.original_language=='en'" 
              src="../assets/images/en.png" 
              alt="bandiera inglese">
            <h2 v-else>{{ movie.original_language }}</h2>
            <h2>{{ movie.vote_average }}</h2>
        </div>
        <div class="serie" v-for="(serie) in series" :key="serie">
            <h2>Serie TV</h2>
            <h2>{{ serie.name }}</h2>
            <h2>{{ serie.original_name }}</h2>
            <img 
              v-if="serie.original_language=='it' "
              src="../assets/images/it.png" 
              alt="bandiera italiana">
            <img
              v-else-if="serie.original_language=='en'" 
              src="../assets/images/en.png" 
              alt="bandiera inglese">
            <h2 v-else>{{ serie.original_language }}</h2>
            <h2>{{ serie.vote_average }}</h2>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Main',
    props: {
        movies: Array,
        series: Array,
    },
    data() {
        return {
            // baseURL: `https://image.tmdb.org/t/p/w342/${this.cover}`
            // finalSrc: ""
        }
    }
    // methods: {
    //     finalUrl: function(index) {
    //         return this.baseURL += this.movies(index).poster_path;
    //     }
    // }
}
</script>

<style lang="scss" scoped>
    div {
        display: flex;
        justify-content: flex-start;
        flex-wrap: wrap;
        overflow: auto;
        height: calc(100vh - 100px);
        background-color: #E94F02;
    }

    .film, .serie {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        width: 15%;
        height: 300px;
        margin: 20px;
        padding-left: 5px;
        background-color: black;
        font-size: 10px;
        color: white;
        img {
            height: 10px;
            width: 15px;
        }
    }

</style>