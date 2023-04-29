<template>
  <div id="container">
    <TrialGraph />
    <TrialTwoVue />
    <TheGraph v-for="(babies, index) in BBN" :key="babies.nm" :id="index + 1" :BBN="babies" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TheGraph from '../components/TheGraph.vue'
import TrialGraph from '../components/TrialGraph.vue'
import TrialTwoVue from '../components/TrialTwo.vue'
const BBN = ref('')
async function fetchData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json()
  BBN.value = data
  console.log(data)
}

onMounted(() => {
  fetchData()
})
</script>

<style scoped>
#container {
  /* background-color: brown; */
}
.cards {
  font-size: 30rem;
  color: black;
  background-color: aqua;
}
</style>
