<template>
  <p></p>
</template>

<script setup>
import { ref, onMounted } from 'vue'
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
