<template>
  <div id="analyse">
    <h2>Analyse du bien</h2>
    <div :class="this.bgPrice()" role="alert">
    <h4 class="alert-heading">Prix du bien</h4>
    <p>À {{ this.results.location }}, le prix moyen d'une maison au m² est de <b>{{ this.analyse.house_average }}€</b> soit {{ this.computePricePercent() }}% {{ this.computePriceDif() }} au prix de ce bien.</p>
    </div>
    <div :class="this.bgAge()" role="alert">
    <h4 class="alert-heading">Année de construction</h4>
    <p>Cette maison <b>est plus {{ this.ageRecently() }} que {{ this.computeAgePercent() }}%</b> des maisons en vente actuellement et a en moyenne <b>{{ this.computeAge() }} ans de {{ this.computeAgeDif() }} que la concurrence</b></p>
    <!-- <hr> -->
    <p class="mb-0">Suite à un achat de ce type, un acquereur {{ this.ageEconomy() }} en moyenne <b>{{ this.analyse.house_age_value[0] }}€ de rénovations en tout genre</b> soit <b>{{ this.computeAgeExpanseAverage() }}</b> que la moyenne pour cette surface</p>
    </div>
    <div :class="this.bgEnergy()" role="alert">
    <h4 class="alert-heading">Classe énergie</h4>
    <p>Cette maison a une <b>classe énergétique {{ this.results.energy }}</b> ce qui est moins bien que {{ this.formatPercentEnergy() }}% des maisons en vente actuellement</p>
    <!-- <hr> -->
    <p class="mb-0">Le surcoût énergétique par m2 est estimé à {{ this.priceEnergeticExpanse() }}€</p>
    </div>
    <div :class="this.bgFinalEvaluation()" role="alert">
    <h4 class="alert-heading">Estimation</h4>
    <p>En prenant en compte l'année de construction, la localisation et le prix au m2 nous pensons que cette maison est {{ this.finalEvaluation() }}.</p>
    <!-- <hr> -->
    <p class="mb-0">Afin de correspondre au prix du marché nous évaluons que le prix de ce bien devrait se situer entre <b>{{ this.computePotentialMinValue() }}€</b> et <b>{{ this.computePotentialMaxValue() }}€</b></p>
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
    computePricePercent: function() {
      console.log(this.results)
      console.log(this.analyse)
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
    },
    computePriceDif: function() {
      if ((this.results.price / this.results.size) < this.analyse.house_average) {
        return "supérieur"
      } else {
        return "inférieur"
      }
    },
    computeAgePercent: function() {
      return (((2021 - this.results.foundation_years) / this.analyse.years_average) * 100).toFixed(2)
    },
    computeAge: function() {
      return 2021 - this.results.foundation_years
    },
    computeAgeDif: function() {
      let houseAge = 2021 - this.results.foundation_years
      let result = ""
      houseAge < this.analyse.years_average ? result += "moins" : result += "plus"
      return result
    },
    ageRecently: function() {
      let isEconomy = this.analyse.house_age_value[1]
      let result = ""
      isEconomy ? result += "récente" : result += "ancienne"
      return result
    },
    ageEconomy: function() {
      let isEconomy = this.analyse.house_age_value[1]
      let result = ""
      isEconomy ? result += "économisera" : result += "dépensera"
      return result
    },
    bgAge: function() {
      let houseAge = 2021 - this.results.foundation_years
      let result = "alert "
      if (houseAge < 10) result += "alert-success"
      if (houseAge < 20 && houseAge > 9) result += "alert-info"
      if (houseAge < 40 && houseAge > 19) result += "alert-warning"
      if (houseAge > 40) result += "alert-danger"
      return result
    },
    computeAgeExpanseAverage: function() {
      let houseValue = this.analyse.house_age_value[0]
      if (houseValue < this.analyse.average_expanse_age) {
        return (this.analyse.average_expanse_age - houseValue) + "€ de moins"
      } else {
        return (houseValue - this.analyse.average_expanse_age) + "€ de plus"
      }
    },
    formatPercentEnergy: function() {
      return this.analyse.percent_energy.toFixed(2)
    },
    priceEnergeticExpanse: function() {
      return (this.analyse.energetic_value[0] / this.results.size).toFixed(1)
    },
    bgEnergy: function() {
      let note = this.results.energy
      let result = "alert "
      if (note == "A" || note == "B") result += "alert-success"
      if (note == "C" || note == "D") result += "alert-info"
      if (note == "E") result += "alert-warning"
      if (note == "F" || note == "G") result += "alert-danger"
      return result
    },
    finalEvaluation: function() {
      if (this.analyse.real_square_meter_price < this.analyse.house_average) {
        return "sous évalué"
      } else {
        return "surévaluée"
      }
    },
    computePotentialMinValue: function() {
      return ((this.analyse.house_average * this.results.size) * 0.9).toFixed(2)
    },
    computePotentialMaxValue: function() {
      return ((this.analyse.house_average * this.results.size) * 1.1).toFixed(2)
    },
    bgFinalEvaluation: function() {
      let priceMeter = this.analyse.real_square_meter_price
      let result = "alert "
      if (priceMeter < this.analyse.house_average) result += " alert-success"
      if (priceMeter >= (this.analyse.house_average * 1.1)) result += " alert-info"
      if (priceMeter >= (this.analyse.house_average * 1.25)) result += " alert-warning"
      if (priceMeter >= (this.analyse.house_average * 1.5)) result += " alert-danger"
      return result
    }
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
