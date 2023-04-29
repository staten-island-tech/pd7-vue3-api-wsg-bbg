<template>
  <div id="container">
    <TrialGraph />
    <TrialTwoVue />
    <TheGraph
      v-for="(babies, index) in BBN"
      :key="babies.nm"
      :id="index + 1"
      :BBN="babies"
      class="cards"
    />
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeMount } from 'vue'
import TheGraph from '../components/TheGraph.vue'
import TrialGraph from '../components/TrialGraph.vue'
import TrialTwoVue from '../components/TrialTwo.vue'
const BBN = ref('')
async function fetchData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json()
  BBN.value = data
}

onBeforeMount(() => {
  fetchData()
})
</script>

<style scoped>
#container {
  background-color: lightskyblue;
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
