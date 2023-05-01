<template>
  <div>
    <h1>{{ graphArray.nm }}</h1>
    <h2>{{ id }}</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  graphArray: Array,
  id: Number
})

const graphArray = ref('')
graphArray.value = [
  {
    nm: PieChart,
    id: 0
  },
  {
    nm: BarChart,
    id: 1
  }
]
</script>

<style scoped></style>
