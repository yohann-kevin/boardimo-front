<template>
  <div id="app">
    <Header/>
    <Search v-on:sendurl="findData"/>
    <Results :data="this.results"/>
    <Analyse :results="this.results" :analyse="this.analyse"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Search from './components/Search.vue'
import Results from './components/Results.vue'
import Analyse from './components/Analyse.vue'

export default {
  name: 'App',
  data() {
    return {
      results: {},
      analyse: {}
    }
  },
  components: {
    Header,
    Search,
    Results,
    Analyse
  },
  methods: {
    findData: function() {
      this.$axios.get("http://localhost:7373/").then(response => (this.formatData(response.data)))
    },
    formatData: function(data) {
      // console.log(data.results)
      this.results = data.results
      this.analyse = data.analyze
    }
  },
  mounted() {
    this.findData()
  },
}
</script>

<style scoped>

</style>
