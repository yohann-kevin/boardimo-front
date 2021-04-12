<template>
  <div>
    <header>
      <img src="../assets/img/logo2.png" alt="logo boardimo">
    </header>

    <section id="search">
      <h1>Analyser un bien immobilier !</h1>
      <div class="center">
      <input type="text" class="form-input rounded text-pink-500 px-5 py-2">
      <button>Lancer l'analyse</button>
      </div>
    </section>

    <section id="results" class="flex shadow-2xl">
      <div class="flex-none w-48 relative">
      <img src="../assets/img/house.png" alt="" class="absolute inset-0 w-full h-full object-cover" />
      </div>
      <form class="flex-auto p-6">
      <div class="flex flex-wrap">
        <h1 class="flex-auto text-xl font-semibold">
        Maison contemporaine au centre de séné
        </h1>
        <div class="text-xl font-semibold text-gray-500">
        718 500 €
        </div>
      </div>
    
        <div class="divide-y divide-fuchsia-300">
          <div><span class="badge bg-primary">165m²</span>   <span class="badge bg-primary">2012</span> <span class="badge bg-d">D</span></div>
          <br>
          <div class="bottom-divide">Prix par m² <span class="price">4363€</span></div>
    
        </div>
        </form>
    </section>

    <section id="analyse">
      <h2>Analyse du bien</h2>
      <div class="alert alert-danger" role="alert">
      <h4 class="alert-heading">Prix du bien</h4>
      <p>À Vannes, le prix moyen d'une maison au m² est de <b>3650€</b> soit 17% inférieur au prix de ce bien.</p>
      </div>
      <div class="alert alert-info" role="alert">
      <h4 class="alert-heading">Année de construction</h4>
      <p>Cette maison <b>est plus récente que 73%</b> des maisons en vente actuellement et a en moyenne <b>8 ans de moins que la concurrence</b></p>
      <!-- <hr> -->
      <p class="mb-0">Suite à un achat de ce type, un acquereur dépensera en moyenne <b>39 600€ de rénovations en tout genre</b> soit <b>17 325€ de moins</b> que la moyenne pour cette surface</p>
      </div>
      <div class="alert alert-warning" role="alert">
      <h4 class="alert-heading">Classe énergie</h4>
      <p>Cette maison a une <b>classe énergétique D</b> ce qui est moins bien que 51% des maisons en vente actuellement</p>
      <!-- <hr> -->
      <p class="mb-0">Le surcoût énergétique par m2 est estimé à 30.4€</p>
      </div>
      <div class="alert alert-danger" role="alert">
      <h4 class="alert-heading">Estimation</h4>
      <p>En prenant en compte l'année de construction, la localisation et le prix au m2 nous pensons que cette maison est surévaluée.</p>
      <!-- <hr> -->
      <p class="mb-0">Afin de correspondre au prix du marché nous évaluons que le prix de ce bien devrait se situer entre <b>552k€</b> et <b>675k€</b></p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
    name: "Home"
}
</script>

<style scoped>
header {
  background-color: #FFF;
  border-bottom: 4px solid #B5443B;
  padding: 20px 0;
}
header img {
  width: 180px;
  margin: 0 auto;
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

/* #search input {
  border: 1px solid #6a9ef2;
  width: 400px;
  height: 40px;
} */

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


.center {
  padding: 10px;
  text-align: center;
}


#results {
  margin: 50px auto;
  width: 60%;
  border-radius: 5px;
  overflow: hidden;
}

span.price {
  color: #1083b1;
  font-weight: bold;
}
.bottom-divide {
  padding-top: 15px;
}


#analyse {
  width: 60%;
  margin: 0 auto;
}

#analyse h2 {
  font-weight: bold;
}

#analyse .alert {
  margin-top: 20px;
}

#analyse h4 {
  font-size: 2em;
  font-weight: bold;
}

#analyse p { 
  padding: 8px;
}

.bg-primary {
  color: #FFF;
}

.bg-a {
  background-color: #09db09;
}
.bg-b {
  background-color: #82c506;
}
.bg-c {
  background-color: #fffb00;
}
.bg-d {
  background-color: #ffae00;
}
.bg-e {
  background-color: #ff7300;
}
.bg-f {
  background-color: #ff5100;
}
.bg-g {
  background-color: #ff0000;
}

.alert-info {
  color: #7c9600;
  background-color: #eef5bf;
  border-color: #d3de8b;
}
.alert-info hr {
  border-top-color: #d3de8b;
}
</style>
