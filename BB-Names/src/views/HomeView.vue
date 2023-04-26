<template>
  <div id="container">
    <sub v-for="babies in BBN.value" :key="babies.nm" class="cards">
      {{ babies }}
    </sub>

    <TheGraph />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TheGraph from '../components/TheGraph.vue'
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
/* export default {} */
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
