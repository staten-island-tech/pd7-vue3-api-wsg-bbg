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
        labels: ['MALE', 'FEMALE'],
        datasets: [{ data: [] }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        backgroundColor: ['#0000FF', '#FFC0CB']
      }
    }
  },
  async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
      const BabyNames = await res.json()
      const male = BabyNames.filter((babies) => babies.gndr === 'MALE')
      this.datas.datasets[0].data.push(male.length)
      const female = BabyNames.filter((babies) => babies.gndr === 'FEMALE')
      this.datas.datasets[0].data.push(female.length)
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style lang="scss" scoped></style>
