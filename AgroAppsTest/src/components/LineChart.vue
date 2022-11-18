<template>
  <Bar :chart-data="chartData" />
  {{ $dailyMax }}
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)


export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    dailyMax: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      chartData: {
        labels: ['Day 1', 'Day 2', 'Day 3', 'Day 4', 'Day 5', 'Day 6', 'Day 7'],
        options: {
          responsive: true,
          maintainAspectRatio: false
        },
        datasets: [
          {
            label: 'max Temperature',
            backgroundColor: '#02075d',
            data: [17, 19, 20, 16, 21, 17, 18]
            // data: this.dailyMax
          }
        ]
      }
    }
  }
}
// console.log(dailyData)
</script>