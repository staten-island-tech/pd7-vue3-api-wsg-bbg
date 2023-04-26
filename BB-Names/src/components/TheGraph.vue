<template>
  <div>
    <h1>{{ BBN.nm }}</h1>
    <h2>{{ id }}</h2>
  </div>
</template>

<script>
export default {
  props: {
    BBN: Object,
    id: Number
  }
}
</script>

<style lang="scss" scoped></style>
