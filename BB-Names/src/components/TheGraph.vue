<template>
  <div>
    <h1>{{ BBN.nm }}</h1>
    <h2>{{ id }}</h2>
  </div>
</template>

<script setup>
const props = defineProps({
  BBN: Object,
  id: Number
})
</script>

<style scoped></style>
