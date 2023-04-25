<template>
  <p>
    <TheGraph />
  </p>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import TheGraph from '../components/TheGraph.vue'
const BBN = ref('')
async function fetchData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json
  BBN.values = data
  console.log(BBN.values)
}

onMounted(() => {
  fetchData()
})
/* export default {} */
</script>

<style scoped></style>
