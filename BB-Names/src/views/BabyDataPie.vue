<template>
  <div id="container">
    <PieGraphVue class="pie" />
  </div>
</template>

<script setup>
import PieGraphVue from '../components/PieGraph.vue'
</script>

<style scoped>
#container {
  display: flex;
  justify-content: center;
  width: 10rem;
}
.pie {
  width: 30rem;
  height: 30rem;
}
nav {
  width: 100%;
  font-size: 1rem;
  text-align: center;
  margin-top: 2rem;
}
