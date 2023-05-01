<template>
  <div>
    <Pie v-if="loaded" :data="datas" :options="options" />
  </div>
</template>

<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'PieChart',
  components: {
    Pie
  },
  data() {
    return {
      loaded: false,
      datas: {
        labels: [
          'ASIAN AND PACIFIC ISLANDER',
          'BLACK NON HISPANIC',
          'HISPANIC',
          'WHITE NON HISPANIC'
        ],
        datasets: [{ data: [] }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        backgroundColor: ['#0000FF', '#FFC0CB', '#A020F0', '#00FF00']
      }
    }
  },
  async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
      const BabyNames = await res.json()
      const api = BabyNames.filter((babies) => babies.ethcty === 'ASIAN AND PACIFIC ISLANDER')
      this.datas.datasets[0].data.push(api.length)
      const bnh = BabyNames.filter((babies) => babies.ethcty === 'BLACK NON HISPANIC')
      this.datas.datasets[0].data.push(bnh.length)
      const h = BabyNames.filter((babies) => babies.ethcty === 'HISPANIC')
      this.datas.datasets[0].data.push(h.length)
      const wnh = BabyNames.filter((babies) => babies.ethcty === 'WHITE NON HISPANIC')
      this.datas.datasets[0].data.push(wnh.length)
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style lang="scss" scoped></style>
