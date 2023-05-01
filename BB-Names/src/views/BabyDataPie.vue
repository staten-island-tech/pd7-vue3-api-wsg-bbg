<template>
  <div class="pieGraph">
    <nav>
      <RouterLink to="/" class="home">Names</RouterLink>
      <RouterLink to="/BabyDataBar/" class="bar">Bar Graph</RouterLink>
    </nav>
    <PieGraphVue class="pieg" />
  </div>
</template>

<script setup>
import PieGraphVue from '../components/PieGraph.vue'
</script>

<style scoped>
.pieg {
  width: 30rem;
  height: 30rem;
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
