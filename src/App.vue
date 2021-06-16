<template>
  <div id="app">
    <Header @cerca="setTerm"/>
    <Main
    :movies="films"
    :series="series"
    :search="searching"
    />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      searchTerm:"",
      films: [],
      series: [],
      searching: false,
    }
  },
  methods: {
    setTerm (setSearch) {
      axios
            .get('https://api.themoviedb.org/3/search/movie', {
              params: {
                api_key: '566ba9ef10ccfee32a5a7380346f0a0a',
                    query: setSearch,
                    language: 'it-IT'
                }
            })
            .then(
              (response) => {
                this.films = response.data.results;
                this.searching = true;
                }
            );
      axios
            .get('https://api.themoviedb.org/3/search/tv', {
              params: {
                api_key: '566ba9ef10ccfee32a5a7380346f0a0a',
                    query: setSearch,
                    language: 'it-IT'
                }
            })
            .then(
              (response) => {
                this.series = response.data.results;
                // console.log(this.series);
                this.searching = true;

                }
            );

            this.searchTerm = setSearch;
    }
  }
}
</script>

<style lang="scss">

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
</style>
