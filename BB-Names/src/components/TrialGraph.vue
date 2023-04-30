<template>
  <Doughnut :v-if="loaded" :data="chartData" :options="chartOptions" />
</template>

<script>
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'

ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'DoughChart',
  components: {
    Doughnut
  },
  data() {
    return {
      loaded: false,
      chartData: { labels: ['Female', 'Male'], datasets: [{ data: [] }] },
      chartOptions: {
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
      this.chartData.datasets[0].data.push(male.length)
      const female = BabyNames.filter((babies) => babies.gndr === 'FEMALE')
      this.chartData.datasets[0].data.push(female.length)
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style></style>
