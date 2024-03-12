<template>
  <table class="table">
    <thead>
      <tr>
        <th>ลำดับ</th>
        <th scope="col">ความชื้น</th>
        <th scope="col">อุณหภูมิ</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(data, index) in dataset" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ data.x }}</td>
        <td>{{ data.y }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: "TableData",
  props: {
    dataset: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<style scoped>
* {
  font-size: 12px;
}
</style>
