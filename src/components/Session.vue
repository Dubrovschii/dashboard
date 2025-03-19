<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Chart } from "chart.js";

const myChart = ref(null);

const chartData = {
  labels: [
    "12 AM",
    "4 PM",
    "11 PM",
    "12 AM",
    "8 AM",
    "8 AM",
    "11 PM",
    "12 AM",
    "4 PM",
    "8 AM",
    "12 AM",
    "4 PM",
    "8 AM",
    "11PM",
  ],
  datasets: [
    {
      label: "Revenue",
      data: [0, 125, 80, 130, 70, 150, 200, 420, 80, 65, 120, 30, 20],
      fill: false,
      borderColor: "#CB3CFF",
      tension: 0.1,
      pointRadius: 0,
      pointBackgroundColor: "#CB3CFF",
      borderWidth: 1,
    },
  ],
};

const chartOptions = {
  responsive: true,
  plugins: {
    legend: {
      display: false,
    },
  },

  scales: {
    x: {
      grid: {
        display: false,
      },
      ticks: {
        autoSkip: true,
        maxTicksLimit: 4,
        callback: (value, index) => {
          const labels = chartData.labels;
          if (index < labels.length) {
            return labels[index];
          }
          return null;
        },
        rotate: 0,
        align: "center",
        color: "#AEB9E1",
        minRotation: 0,
        maxRotation: 0,
        autoSkipPadding: 5,
        autoRotation: false,
        font: {
          size: 8,
          lineHeight: 1.2,
          weigth: 400,
        },
      },
    },
    y: {
      suggestedMin: 0,
      suggestedMax: 500,
      min: 0,
      max: 500,
      ticks: {
        stepSize: 50,
        callback: (value) => {
          if (value === 0 || value === 100 || value === 250 || value === 500) {
            return `${value}`;
          }
          return null;
        },
      },
      grid: {
        display: false,
      },
    },
  },
};

let chartInstance = null;

onMounted(() => {
  const ctx = myChart.value.getContext("2d");
  chartInstance = new Chart(ctx, {
    type: "line",
    data: chartData,
    options: chartOptions,
  });
});

onBeforeUnmount(() => {
  if (chartInstance) {
    chartInstance.destroy();
  }
});
</script>

<template>
  <canvas ref="myChart"></canvas>
</template>

<style scoped></style>
