<template>
  <nav>
    <RouterLink to="/" class="home">Names</RouterLink>
    <RouterLink to="/BabyDataPie/" class="pie">Pie Graph</RouterLink>
  </nav>
  <div class="barGraph">
    <BarGraphVue class="barg" />
  </div>
</template>

<script setup>
import BarGraphVue from '../components/BarGraph.vue'
</script>

<style scoped>
.barGraph {
  margin: auto;
  width: 75%;
}
.barg {
  width: 30rem;
  height: 30rem;
  margin-left: auto;
  margin-right: auto;
}
nav {
  width: 100%;
  font-size: 1rem;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: pink;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid blue;
}

nav a:first-of-type {
  border: 0;
}
</style>
