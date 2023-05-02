<template>
  <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/BabyDataBar/">BarGraph</RouterLink>
  </nav>
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
  width: 80vw;
  height: 70vh;
}
.pie {
  width: 50rem;
  height: 30rem;
}
nav {
  width: 100%;
  font-size: 1rem;
  text-align: center;
  margin-top: 2rem;
  width: 70rem;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
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
