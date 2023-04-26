<template>
  <p>
    <TheGraph v-for="(babies, index) in BBN" :key="babies.nm" :id="index + 1" :BBN="babies" />
  </p>
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
