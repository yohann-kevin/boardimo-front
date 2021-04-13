<template>
    <div id="search">
      <h1>Analyser un bien immobilier !</h1>
      <div class="center">
      <input type="text" class="form-input rounded text-pink-500 px-5 py-2">
      <button>Lancer l'analyse</button>
      </div>
    </div>
</template>

<script>
export default {
    name: "Search"
}
</script>

<style scoped>
.center {
  padding: 10px;
  text-align: center;
}

#search {
  background: rgb(226,235,245);
  background: linear-gradient(0deg, rgba(226,235,245,1) 0%, rgba(255,255,255,1) 100%);
  margin: 0 auto;
  padding: 10px 0 50px;
}

#search h1 {
  text-align: center;
  color: #04275e;
  font-weight: bold;
  font-size: 2em;
  margin-top: 100px;
  padding-bottom: 20px;
}

#search button {
  color: #FFF;
  background-color: #1083b1;
  border: 1px solid #165872;
  padding: 6px;
  border-radius: 3px;
}

#search button:hover {
  background-color: #044b68;
  border: 1px solid #000;
  padding: 6px;
  border-radius: 3px;
}
</style>
