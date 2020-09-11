<template>
  <div>
    <div class="skills-content">
      <div class="skills-header fadeInDown animated">
        <button :class="{ 'active-btn': chart == 1 }" @click="chart = 1">
          <i class="fas fa-code" style="font-size: 18px;"></i>
          <p style="font-size: 10px; font-family:comfortaa;">CODING</p>
        </button>
        <button :class="{ 'active-btn': chart == 2 }" @click="chart = 2">
          <i class="far fa-object-group" style="font-size: 18px;"></i>
          <p style="font-size: 10px;font-family:comfortaa;">GRAPHICS</p>
        </button>
      </div>

      <div class="chart1-container" v-show="chart == 1">
        <canvas id="codingChart" width="300" height="300"></canvas>
      </div>

      <div class="chart2-container" v-show="chart == 2">
        <canvas id="graphicsChart" width="300" height="300"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
import Chart from "chart.js";

Chart.defaults.global.defaultFontColor = "white";
Chart.defaults.global.defaultStrokeColor = "white";

export default {
  name: "skills",
  data() {
    return {
      chart: 2,
    };
  },
  methods: {
    show: () => {
      console.log("chart");
    },
  },
  mounted() {
    Chart.defaults.global.defaultFontFamily = "comfortaa";

    var ctx = document.getElementById("codingChart");
    new Chart(ctx, {
      type: "radar",

      data: {
        labels: [
          "VueJS",
          "ReactJS",
          "Angular 8",
          "NodeJS",
          "ExpressJS",
          "JAVA",
          "Python",
          "HTML",
          "CSS",
          "MongoDB",
          "MySQL",
          "WordPress",
          "Git",
        ],
        datasets: [
          {
            label: "# of Votes",
            data: [7.5, 7.5, 8.5, 9, 9, 5.5, 5.5, 9, 9, 8.5, 7.5, 6.5, 6.5],

            backgroundColor: ["rgba(253,221,231,0.3)"],
            borderColor: "#f0355d",
            borderWidth: 3,
          },
        ],
      },
      options: {
        
        responsive: true,
        scale: {
          ticks: {
            display: false,
            beginAtZero: true,
            max: 10,
          },
          pointLabels: {
            fontSize: 13,
          },
          gridLines: {
            color: "#a39bde",
          },
          angleLines: {
            color: "#a39bde",
          },
        },
        legend: {
          display: false,
        },

        tooltips: {
          enabled: false,
        },
      },
    });

    // graphics chart
    var ctx2 = document.getElementById("graphicsChart");
    new Chart(ctx2, {
      type: "radar",
      data: {
        labels: ["Photoshop", "Illustrator", "After effect", "Xdesign"],
        datasets: [
          {
            label: "# of Votes",
            data: [4.5, 4, 3, 3],
            backgroundColor: ["rgba(253,221,231,0.3)"],
            borderColor: "#f0355d",
            borderWidth: 3,
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scale: {
          ticks: {
            display: false,
            beginAtZero: true,
            max: 5,
          },
          pointLabels: {
            fontSize: 13,
          },
          gridLines: {
            color: "#a39bde",
          },
          angleLines: {
            color: "#a39bde",
          },
        },
        legend: {
          display: false,
        },
        tooltips: {
          enabled: false,
        },
      },
    });
  },
};
</script>

<style lang="scss" scoped>
@import url("https://use.fontawesome.com/releases/v5.0.13/css/all.css");

.skills-content {
  height: 90vh;
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  text-align: center;
  font-family: comfortaa;
}

.skills-header > .active-btn {
  background: royalblue;
  transition: all 0.2s;
}

.skills-header > button {
  background-color: transparent;
  text-align: center;
  border: none;
  cursor: pointer;
  outline: none;
  font-size: 20px;
  margin-left: 5px;
  color: #645f8a;
}

.skills-header > .active-btn {
  background-color: transparent;
  text-align: center;
  border: none;
  cursor: pointer;
  outline: none;
  margin-left: 0px;
  color: #ff4d5a;
}

.chart1-container {
  position: relative;
  margin: 0 auto;
  width: 320px;
  height: 320px;
  font-family: comfortaa;
}
.chart2-container {
  position: relative;
  width: 320px;
  height: 320px;
  margin: 0 auto;
  font-family: comfortaa;
}
</style>
