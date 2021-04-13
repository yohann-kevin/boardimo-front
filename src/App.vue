<template>
  <div id="app">
    <Header/>
    <Search/>
    <Results/>
    <Analyse/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Search from './components/Search.vue'
import Results from './components/Results.vue'
import Analyse from './components/Analyse.vue'

export default {
  name: 'App',
  components: {
    Header,
    Search,
    Results,
    Analyse
  }
}
</script>

<style scoped>

</style>
