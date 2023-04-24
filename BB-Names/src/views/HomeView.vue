<template>
  <p></p>
</template>

<script setup>
import { ref, onMounted } from 'vue'
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
