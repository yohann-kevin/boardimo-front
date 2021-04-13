<template>
    <div id="results" class="flex shadow-2xl">
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
    </div>
</template>

<script>
export default {
    name: "Results"
}
</script>

<style scoped>
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
