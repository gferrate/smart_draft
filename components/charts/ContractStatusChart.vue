<template>
  <pie-chart :data="barChartData" :options="barChartOptions" :height="240" :width="220"/>
</template>

<script>
import PieChart from "~/components/PieChart";

const chartColors = {
  red: "rgb(255, 99, 132)",
  orange: "rgb(255, 159, 64)",
  yellow: "rgb(255, 205, 86)",
  green: "rgb(75, 192, 192)",
  blue: "rgb(54, 162, 235)",
  purple: "rgb(153, 102, 255)",
  grey: "rgb(201, 203, 207)"
};

export default {
  props: ["data", "title", "labels"],
  data() {
    return {
      barChartData: {
        labels: this.labels,
        datasets: [
          {
            label: "Income",
            backgroundColor: [
              chartColors.blue,
              chartColors.purple,
              chartColors.grey
            ],
            data: this.data
          }
        ]
      },
      barChartOptions: {
        responsive: false,
        legend: {
          display: true
        },
        title: {
          display: true,
          text: this.title
        }
        /*scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true
              }
            }
          ]
        }*/
      }
    };
  },
  components: {
    PieChart
  }
};
</script>
