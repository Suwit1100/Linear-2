<template>
  <div class="container">
    <div class="row mt-5">
      <div class="col-6">
        <div class="form-floating mb-3">
          <input
            type="number"
            class="form-control"
            id="number1"
            v-model="moisture"
          />
          <label for="number1">ข้อมูลความชื่น</label>
        </div>
        <div class="form-floating">
          <input
            type="number"
            class="form-control"
            id="number2"
            v-model="temperature"
          />
          <label for="number2">ข้อมูลอุณหภูมิ</label>
        </div>
        <div class="mt-2">
          <button
            class="btn btn-success form-control"
            :disabled="isButtonDisabled"
            @click="addData"
          >
            เพิ่มข้อมูล
          </button>
        </div>
        <div class="mt-5">สมการในการสร้าง Linear y = mx + b</div>
        m = "" b = ""
        <div class="mt-3">
          <button class="btn btn-success form-control" @click="Calculate">
            คำนวณ
          </button>
        </div>
      </div>
      <div class="col-6">
        <TableData :dataset="dataset" />
      </div>
    </div>
  </div>
</template>
<script>
import TableData from "./components/TableData";
export default {
  name: "App",
  data() {
    return {
      moisture: null,
      temperature: null,
      dataset: [],
      keydataset: 0,
      sumx: null,
      sumy: null,
      meanx: null,
      meany: null,
      obj: null,
      x: null,
      y: null,
      num: null,
      denom: null,
      m: null,
      b: null,
    };
  },
  methods: {
    addData() {
      this.dataset.push({
        x: this.moisture,
        y: this.temperature,
      });
      this.moisture = null;
      this.temperature = null;
    },
    Calculate() {
      console.log(2222);

      // คำนวน sum
      this.dataset.forEach((data) => {
        this.sumx += data.x;
      });
      this.dataset.forEach((data) => {
        this.sumy += data.y;
      });

      // คำนวน mean
      this.meanx = this.sumx / this.dataset.length;
      this.meany = this.sumy / this.dataset.length;

      // คำนวณ num denum
      for (
        this.keydataset;
        this.keydataset < this.dataset.length;
        this.keydataset++
      ) {
        this.obj = this.dataset[this.keydataset];
        this.x = this.obj.x;
        this.y = this.obj.y;
        this.num += (this.x - this.meanx) * (this.y - this.meany);
        this.denom += (this.x - this.meanx) * (this.x - this.meanx);
      }
      this.m = this.num / this.denom;
      this.b = this.meany - this.m * this.meanx;

      console.log(
        "ค่า sumx = " +
          this.sumx +
          "\n" +
          "ค่า sumy = " +
          this.sumy +
          "\n" +
          "ค่า meanx = " +
          this.meanx +
          "\n" +
          "ค่า meany = " +
          this.meany +
          "\n" +
          "ค่า m = " +
          this.m +
          "\n" +
          "ค่า b = " +
          this.b +
          "\n"
      );
    },
  },
  computed: {
    isButtonDisabled() {
      return (
        (this.temperature == null && this.temperature == null) ||
        (this.temperature == "" && this.temperature == "")
      );
    },
  },
  components: {
    TableData,
  },
};
</script>
<style></style>
