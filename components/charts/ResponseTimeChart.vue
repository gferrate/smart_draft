<template>
  <bar-chart :data="barChartData" :options="barChartOptions" :height="250" :width="280"/>
</template>

<script>
import BarChart from "~/components/BarChart";

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
            label: "Amount",
            backgroundColor: [
              chartColors.blue,
              chartColors.purple,
              chartColors.gray
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
        },
        scales: {
          yAxes: [
            {
              gridLines: {
                display: true
              },
              ticks: {
                min: 2,
                max: 5
              }
            }
          ]
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
    BarChart
  }
};
</script>
