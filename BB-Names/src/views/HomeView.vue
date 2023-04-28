<template>
  <div id="container">
    <TrialGraph />
    <TheGraph v-for="(babies, index) in BBN" :key="babies.nm" :id="index + 1" :BBN="babies" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TheGraph from '../components/TheGraph.vue'
import TrialGraph from '../components/TrialGraph.vue'
const BBN = ref('')
async function fetchData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json()
  BBN.value = data
  console.log(BBN.value)
}

onMounted(() => {
  fetchData()
})

const hate = ['a', 'a', 'a', 'a']
export default { name: 'App', components: { TrialGraph, TheGraph } }
</script>

<style scoped>
#container {
  background-color: brown;
}
.cards {
  font-size: 30rem;
  color: black;
  background-color: aqua;
}
</style>
