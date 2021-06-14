<template>
    <div>
        <div class="film" v-for="(movie, index) in movies" :key="index">
            <h1>{{ movie.title }}</h1>
            <h2>{{ movie.original_title }}</h2>
            <h2>{{ movie.original_language }}</h2>
            <h2>{{ movie.vote_average }}</h2>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Main',
    props: {
        movies: Array
    },
    data() {
        return {
        }
    }
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

    .film {
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
    }

</style>