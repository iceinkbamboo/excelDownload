<template>
  <div class="box">
    <ExcelDownLoad
      :titleArray="titleArray"
      :excelArray="excelArray"
    ></ExcelDownLoad>
  </div>
</template>

<script>
import ExcelDownLoad from "../components/excelDownload";
export default {
  name: "home",
  components: { ExcelDownLoad },
  data() {
    return {
      titleArray: ["姓名", "年龄", "家庭住址"],
      excelArray: [
        {
          name: "张三",
          age: "18",
          address: "昌平区，第二街道"
        },
        {
          name: "里斯",
          age: "28",
          address: "海淀区，第四街道"
        },
        {
          name: "王五",
          age: "23",
          address: "通州区"
        }
      ]
    };
  },
  methods: {}
};
</script>

<style lang="less" scoped></style>
