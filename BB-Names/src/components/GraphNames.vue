<template>
  <div>
    <h1>{{ BBN.nm }}</h1>
    <h2>{{ BBN.gndr }}</h2>
    <h3>{{ BBN.ethcty }}</h3>
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
