<template>
  <div id="app">
    <Header/>
    <Search v-on:sendurl="findData"/>
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
  },
  methods: {
    findData: function() {
      this.$axios.get("http://localhost:7373/").then(response => (this.formatData(response.data)))
    },
    formatData: function(data) {
      console.log(data)
    }
  },
  mounted() {
    this.findData()
  },
}
</script>

<style scoped>

</style>
