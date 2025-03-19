<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Chart, registerables } from "chart.js";
import arrowUp from "../assets/img/ArrowGreen.svg";

Chart.register(...registerables);

const myChart = ref(null);
let chartInstance = null;

let customDiv = null;
onMounted(() => {
  if (myChart.value) {
    myChart.value.style.height = "394px";
  }
  if (!myChart.value) return;
  const ctx = myChart.value.getContext("2d");

  const gradientRevenue = ctx.createLinearGradient(0, 0, 0, 400);
  gradientRevenue.addColorStop(0, "rgba(203, 60, 255, 0.2)");
  gradientRevenue.addColorStop(1, "rgba(203, 60, 255, 0)");

  const gradientExpenses = ctx.createLinearGradient(0, 0, 0, 400);
  gradientExpenses.addColorStop(0, "rgba(0, 194, 255, 0.2)");
  gradientExpenses.addColorStop(1, "rgba(0, 194, 255, 0)");

  chartInstance = new Chart(ctx, {
    type: "line",
    data: {
      labels: [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec",
      ],
      datasets: [
        {
          label: "Revenue",
          data: [0, 10, 45, 85, 94, 100, 110.8, 125.2, 150, 120, 170, 240.4],
          borderColor: "#CB3CFF",
          backgroundColor: gradientRevenue,
          fill: true,
          tension: 0.4,
          pointRadius: (ctx) => (ctx.dataIndex === 5 ? 5 : 0),
          pointBorderColor: "#CB3CFF",
          pointBackgroundColor: "#0b1739",
          pointBorderWidth: 1,
          borderWidth: 1,
        },
        {
          label: "Expenses",
          data: [27, 35, 20, 30, 70, 85, 57, 165, 130, 65, 50, 80],
          borderColor: "#00C2FF",
          backgroundColor: gradientExpenses,
          fill: true,
          tension: 0.4,
          pointRadius: 0,
          pointHoverRadius: 1,
          pointBackgroundColor: "#00C2FF",
          pointBorderWidth: 1,
          borderWidth: 1,
        },
      ],
    },
    options: {
      responsive: true,
      plugins: {
        legend: {
          display: false,
        },
        tooltip: {
          enabled: true,
          backgroundColor: "rgba(0,0,0,0.8)",
          bodyFont: {
            size: 14,
          },
          callbacks: {
            label: function (tooltipItem) {
              return `$${tooltipItem.raw.toFixed(1)}k`;
            },
          },
        },
      },
      scales: {
        x: {
          grid: {
            display: false,
          },
          ticks: {
            rotate: 0,
            align: "center",
            color: "#AEB9E1",
            minRotation: 0,
            maxRotation: 0,

            autoRotation: false,
            font: {
              size: 10,
              lineHeight: 1.4,
              weigth: 400,
            },
          },
        },
        y: {
          suggestedMin: 0,
          suggestedMax: 250,
          min: 0,
          max: 250,
          ticks: {
            stepSize: 25,
            callback: (value) => {
              if (value === 0 || value === 25 || value % 50 === 0) {
                return `${value}K`;
              }
              return null;
            },
            align: "center",
            color: "#AEB9E1",
            minRotation: 0,
            maxRotation: 0,

            autoRotation: false,
            font: {
              size: 12,
              lineHeight: 1.4,
              weigth: 400,
            },
          },
          grid: {
            display: false,
          },
        },
      },
      animation: {
        onComplete: () => positionCustomDiv(),
      },
    },
  });
  createCustomDiv();
});

onBeforeUnmount(() => {
  if (chartInstance) chartInstance.destroy();
});
// function createCustomDiv() {
//   customDiv = document.createElement("div");
//   customDiv.classList.add("custom-label");
//   customDiv.innerText = "125.2K";
//   document.body.appendChild(customDiv);
//   console.log(customDiv);

// }
function createCustomDiv() {
  customDiv = document.createElement("div");
  customDiv.classList.add("custom-label");

  const dataBlockTitle = document.createElement("div");
  dataBlockTitle.classList.add("total__block_data");
  dataBlockTitle.innerText = "June 21, 2023";
  const totalBlockTitle = document.createElement("div");
  totalBlockTitle.classList.add("total__block_title");

  const cashDiv = document.createElement("div");
  cashDiv.classList.add("cash");
  cashDiv.innerText = "$125.2k";

  const percentDiv = document.createElement("div");
  percentDiv.classList.add("percent", "percent_green");

  const percentText = document.createTextNode("12.5% ");
  percentDiv.appendChild(percentText);

  const img = document.createElement("img");
  img.src = arrowUp;
  img.alt = "";
  percentDiv.appendChild(img);

  totalBlockTitle.appendChild(cashDiv);
  totalBlockTitle.appendChild(percentDiv);
  customDiv.appendChild(dataBlockTitle);

  customDiv.appendChild(totalBlockTitle);

  const grafic = document.querySelector(".diagram");
  grafic.appendChild(customDiv);
}
function positionCustomDiv() {
  if (!chartInstance || !customDiv) return;

  const dataset = chartInstance.getDatasetMeta(0);
}
// function positionCustomDiv() {
//   if (!chartInstance || !customDiv) return;

//   const dataset = chartInstance.getDatasetMeta(0);
//   const point = dataset.data[7]; // Точка для значения 125.2K

//   if (point) {
//     const rect = myChart.value.getBoundingClientRect();
//     customDiv.style.left = `${
//       rect.left + point.x - customDiv.offsetWidth / 2
//     }px`;
//     customDiv.style.top = `${rect.top + point.y - 20}px`;
//     customDiv.style.opacity = 1;
//   }
// }
</script>

<template>
  <canvas ref="myChart" class="grafic" height="394"></canvas>
</template>

<style lang="scss">
.grafic {
  margin-top: 28px;
  width: 593px !important;
  height: 394px !important;
  object-fit: unset;
}
.custom-label {
  position: absolute;
  top: calc(50% + 30px);
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-flow: column-reverse;
  .total__block_title {
    display: flex;
    .cash {
      font-size: 16px;
      line-height: 18px;
      font-weight: 500;
      color: var(--color-white);
    }
    .percent {
      font-size: 10px;
      line-height: 14px;
      font-weight: 400;
      padding: 2px 4px;
      margin-left: 6px;
      border-radius: 2px;
      height: 20px;
      &_green {
        background-color: rgba(5, 193, 104, 0.2);
        border: 1px solid rgba(5, 193, 104, 0.2);
        color: #14ca74;
      }
      &_red {
        background-color: rgba(255, 90, 101, 0.2);

        border: 1px solid rgba(255, 90, 101, 0.2);
        color: #ff5a65;
      }
    }
  }
  .total__block_data {
    font-size: 10px;
    font-weight: 500;
    line-height: 14px;
    color: #aeb9e1;
  }
}
.diagram {
  position: relative;
}
</style>
