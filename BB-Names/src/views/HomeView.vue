<template>
  <div id="container">
    <PieGraphVue />
    <BarGraphVue />
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue'
import GraphNames from '../components/GraphNames.vue'
import BarGraphVue from '../components/BarGraph.vue'
import PieGraphVue from '../components/PieGraph.vue'

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
  font-size: 1rem;
  color: black;
  background-color: aqua;
  margin: 1rem;
}
</style>
