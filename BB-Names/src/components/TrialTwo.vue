<template>
  <div>
    <Pie v-if="loaded" :data="data" :options="options" />
  </div>
</template>

<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'ChartPie',
  components: {
    Pie
  },
  data() {
    return {
      loaded: false,
      datasets: {
        labels: ['MALE', 'FEMALE'],
        backgroundColor: ['#0000FF', '#FFC0CB'],
        data: {}
      },
      options: {
        responsive: true,
        maintainAspectRatio: false
      }
    }
  },
  async mounted() {
    this.loaded = false
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
      const BabyNames = await res.json()
      const male = BabyNames.filter((babies) => babies.gndr === 'MALE')
      this.datasets.data.push(male.length)
      const female = BabyNames.filter((babies) => babies.gndr === 'FEMALE')
      this.datasets.data.push(female.length)
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style lang="scss" scoped></style>
