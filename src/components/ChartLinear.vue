<template>
  <div class="mt-3">
    <button @click="appendCode">แสดงกราฟ</button>
    <div v-html="dynamicHTML"></div>
  </div>
</template>

<script>
import Chart from "chart.js/auto";
export default {
  name: "ChartLinear",
  data() {
    return {
      dataset2: [],
      dynamicHTML: "",
    };
  },
  props: {
    dataset: {
      type: Array,
      default: () => [],
    },
    regression: {
      type: Array,
      default: () => [],
    },
  },
  mounted() {
    const ctx = document.getElementById("acquisitions").getContext("2d");
    new Chart(ctx, {
      type: "scatter",
      data: {
        datasets: [
          {
            label: "Scatter Dataset",
            data: this.dataset,
            backgroundColor: "red",
          },
          {
            label: "Line Dataset",
            data: [
              { x: 1, y: 3 },
              { x: 2, y: 5 },
              { x: 3, y: 8 },
              { x: 4, y: 10 },
            ],
            borderColor: "blue",
            fill: false,
            type: "line",
          },
        ],
      },
      options: {
        scales: {
          x: {
            type: "linear",
            position: "bottom",
          },
          y: {
            type: "linear",
            position: "left",
          },
        },
      },
    });
  },
  methods: {
    appendCode() {
      // โค้ดที่คุณต้องการเพิ่ม
      const newHTML = '<p style="color: blue;">Appended HTML</p>';
      // เพิ่มโค้ดใน dynamicHTML
      this.dynamicHTML += newHTML;
    },
  },
};
</script>
<style lang=""></style>
