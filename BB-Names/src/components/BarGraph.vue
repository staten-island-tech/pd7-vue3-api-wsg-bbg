<template>
  <div>
    <Bar :data="datas" :options="options" v-if="loaded" />
  </div>
</template>

<script>
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'
import { Bar } from 'vue-chartjs'
ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

export default {
  name: 'BarChart',
  components: {
    Bar
  },
  data() {
    return {
      loaded: false,
      //this won't show sob//
      datas: {
        labels: ['MALE', 'FEMALE'],
        datasets: [{ label: 'Number of Popular Baby Names by Gender', data: [] }]
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
