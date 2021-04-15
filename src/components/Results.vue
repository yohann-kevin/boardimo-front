<template>
    <div ref="results" id="results" class="flex shadow-2xl">
      <div class="flex-none w-48 relative">
        <img :src="this.data.images" alt="" class="absolute inset-0 w-full h-full object-cover" />
      </div>
      <form class="flex-auto p-6">
        <div class="flex flex-wrap">
          <h1 class="flex-auto text-xl font-semibold">
          {{ this.data.title }}
          </h1>
          <div class="text-xl font-semibold text-gray-500">
          {{ this.data.price }} €
          </div>
        </div>
    
        <div class="divide-y divide-fuchsia-300">
          <div>
            <span class="badge bg-primary">{{ this.data.size }}m²</span>   
            <span class="badge bg-primary">{{ this.data.foundation_years }}</span> 
            <span ref="badge" :class="this.formatEnergyNote()">{{ this.data.energy }}</span>
          </div>
          <br>
          <div class="bottom-divide">Prix par m² <span class="price">{{ this.computeMeterPrice(this.data.price, this.data.size) }} €</span></div>
        </div>
      </form>
    </div>
</template>

<script>
export default {
    name: "Results",
    props: {
      data: Object
    },
    methods: {
      computeMeterPrice: function(price, size) {
        return (price / size).toFixed(2)
      },
      formatEnergyNote: function() {
        let result = "badge "
        if (this.data.energy == "A") result += "bg-a"
        if (this.data.energy == "B") result += "bg-b"
        if (this.data.energy == "C") result += "bg-c"
        if (this.data.energy == "D") result += "bg-d"
        if (this.data.energy == "E") result += "bg-e"
        if (this.data.energy == "F") result += "bg-f"
        if (this.data.energy == "G") result += "bg-g"
        return result
      }
    }
}
</script>

<style scoped>
#results {
  margin: 50px auto;
  width: 60%;
  border-radius: 5px;
  overflow: hidden;
  /* display: none; */
}

span.price {
  color: #1083b1;
  font-weight: bold;
}

.bottom-divide {
  padding-top: 15px;
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
