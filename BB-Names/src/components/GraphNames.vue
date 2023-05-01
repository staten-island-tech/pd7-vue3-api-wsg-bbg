<template>
  <div>
    <!-- <nav>
      <router-link :to="babyPath">
        <h1>{{ BBN.nm }}</h1>
        <h2>{{ id }}</h2>
      </router-link>
    </nav> -->

    <h1>{{ BBN.nm }}</h1>
    <h2>{{ BBN.gndr }}</h2>
    <h3>{{ BBN.ethcty }}</h3>
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
