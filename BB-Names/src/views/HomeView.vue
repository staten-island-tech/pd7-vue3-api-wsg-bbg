<template>
  <div id="container">
    <nav>
      <RouterLink to="/BabyDataBar/" class="bar">Bar Graph</RouterLink>
      <RouterLink to="/BabyDataPie/" class="pie">Pie Graph</RouterLink>
    </nav>
    <GraphNames
      v-for="babies in BBN"
      :key="babies.nm"
      :BBN="babies"
      :gndr="babies.gnder"
      :ethcty="babies.ethcty"
      class="cards"
    />
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue'
import GraphNames from '../components/GraphNames.vue'

const BBN = ref('')
async function fetchData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json()
  BBN.value = data
  console.log(data)
}

onBeforeMount(() => {
  fetchData()
})
</script>

<style scoped>
#container {
  /* background-color: lightskyblue; */
  /* ---------------------- */
  width: 70rem;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.cards {
  color: black;
  background-color: lightpink;
  font-size: 1rem;
  margin: 1rem;
  width: 15rem;
  padding: 1rem;
  border-radius: 1rem;
  text-align: center;
}
nav {
  width: 100%;
  font-size: 1rem;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: pink;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid blue;
}

nav a:first-of-type {
  border: 0;
}
</style>
