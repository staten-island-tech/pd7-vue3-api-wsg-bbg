<template>
  <div id="container">
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
  background-color: cyan;
  font-size: 1rem;
  margin: 1rem;
  width: 12rem;
  height: 12rem;
  border-radius: 1rem;
  text-align: center;
}
</style>
