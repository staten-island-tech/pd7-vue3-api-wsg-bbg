<template>
  <div>
    <h1>{{ BBN.nm }}</h1>
    <h2>{{ id }}</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  BBN: Array,
  id: Number
})
</script>

<style scoped></style>
