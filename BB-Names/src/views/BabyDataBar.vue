<template>
  <div id="container">
    <BarGraphVue class="bar" />
  </div>
</template>

<script setup>
import BarGraphVue from '../components/BarGraph.vue'
</script>

<style scoped>
#container {
  display: flex;
  justify-content: center;
  width: 10rem;
}
.bar {
  width: 30rem;
  height: 30rem;
}
</style>
