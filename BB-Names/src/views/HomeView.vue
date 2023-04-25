<template>
  <div>
    <sub v-for="babies in BBN.value" :key="babies">
      {{ babies.nm }}
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
/* export default {} */
</script>

<style scoped></style>
