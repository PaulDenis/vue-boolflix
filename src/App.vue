<template>
  <div id="app">
    <Header @cerca="setTerm" />
    <Main
    :searching="searchTerm"
    />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      searchTerm:""
    }
  },
  methods: {
    setTerm (setSearch) {
      this.SearchTerm = setSearch;
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
