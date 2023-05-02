<template>
  <div>
    <h1 class="test"></h1>
    <BarGraphVue /> <PieGraphVue />
  </div>
</template>

<script>
import { BarGraphVue } from '../components/BarGraph.vue'
import { PieGraphVue } from '../components/PieGraph.vue'
export default {
  data() {
    return {
      babies: {}
    }
  },
  mounted: async function () {
    await this.fetchData()
  },
  methods: {
    fetchData: async function () {
      let res = await fetch(
        `https://data.cityofnewyork.us/resource/25th-nujf.json/${this.$route.params.id}`
      )
      let data = await res.json()
      this.babies = data
    }
  }
}
</script>

<style scoped>
.test {
  font-size: 10rem;
  color: wheat;
}
</style>
