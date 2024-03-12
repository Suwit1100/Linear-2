<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <canvas id="acquisitions"></canvas>
</template>

<script>
import Chart from "chart.js/auto";
export default {
  name: "App",
  components: {},
  mounted() {
    let sdf = 5;
    console.log(sdf);
    (async function () {
      const data = [
        { year: 2010, count: 10 },
        { year: 2011, count: 20 },
        { year: 2012, count: 15 },
        { year: 2013, count: 25 },
        { year: 2014, count: 22 },
        { year: 2015, count: 30 },
        { year: 2016, count: 28 },
      ];

      new Chart(document.getElementById("acquisitions"), {
        type: "bar",
        data: {
          labels: data.map((row) => row.year),
          datasets: [
            {
              label: "Acquisitions by year",
              data: data.map((row) => row.count),
            },
          ],
        },
      });
    })();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
