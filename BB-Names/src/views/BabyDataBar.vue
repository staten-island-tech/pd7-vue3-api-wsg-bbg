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
nav {
  width: 100%;
  font-size: 1rem;
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
