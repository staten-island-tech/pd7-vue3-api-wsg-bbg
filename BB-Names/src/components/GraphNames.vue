<template>
  <div>
    <!-- <nav>
      <router-link :to="babyPath">
        <h1>{{ BBN.nm }}</h1>
        <h2>{{ id }}</h2>
      </router-link>
    </nav> -->
    <h2>{{ BBN.nm }}</h2>
    <h3>{{ BBN.gndr }}</h3>
    <h4>{{ BBN.ethcty }}</h4>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  BBN: Object,
  id: Number
})

const babyPath = computed(() => {
  return `/BabyDataGeneral/${props.BBN.nm}`
})
</script>

<style scoped></style>
