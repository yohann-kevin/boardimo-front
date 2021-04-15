<template>
  <div id="analyse">
    <h2>Analyse du bien</h2>
    <div :class="this.bgPrice()" role="alert">
    <h4 class="alert-heading">Prix du bien</h4>
    <p>À {{ this.price[0] }}, le prix moyen d'une maison au m² est de <b>{{ this.price[1] }}€</b> soit {{ this.price[2] }}% inférieur au prix de ce bien.</p>
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
  </div>
</template>

<script>
export default {
  name: "Analyse",
  props: {
    results: Object,
    analyse: Object
  },
  methods: {
    price: function() {
      return [
        this.results.location,
        this.analyse.house_average,
        this.computePricePercent()
      ]
    },
    cumputePricePercent: function() {
      return (((this.results.price / this.results.size) / this.analyse.house_average) * 100).toFixed(2)
    },
    bgPrice: function() {
      let result = "alert "
      let meterPrice = this.results.price / this.results.size
      if (meterPrice < (this.analyse.house_average * 0.75)) result += "alert-success"
      if ((this.analyse.house_average * 0.75) <= meterPrice) result += "alert-info"
      if ((this.analyse.house_average * 1.25) <= meterPrice) result += "alert-warning"
      if (meterPrice >= (this.analyse.house_average * 1.5)) result += "alert-danger"
      return result
    }
  },
  updated() {
    this.price
  }
}
</script>

<style scoped>
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
</style>
