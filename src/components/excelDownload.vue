<template>
  <div class="hello">
    <button @click="downloadExcel">下载Excel</button>
  </div>
</template>

<script>
import XLSX from "xlsx";
export default {
  name: "HelloWorld",
  props: {
    titleArray: {
      type: Array,
      default() {
        return [];
      }
    },
    excelArray: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  methods: {
    downloadExcel() {
      this.exportExcel(this.titleArray, this.excelArray, "重点项目");
    },
    exportExcel(title, json, name) {
      var data = new Array();
      var titleArray = title;

      for (const key1 in json) {
        if (json.hasOwnProperty(key1)) {
          const element = json[key1];
          var rowDataArray = new Array();
          for (const key2 in element) {
            if (element.hasOwnProperty(key2)) {
              const element2 = element[key2];
              rowDataArray.push(element2);
            }
          }
          data.push(rowDataArray);
        }
      }
      data.splice(0, 0, titleArray);
      console.log(data);
      const ws = XLSX.utils.aoa_to_sheet(data);
      const wb = XLSX.utils.book_new();
      XLSX.utils.book_append_sheet(wb, ws, "SheetJS");
      XLSX.writeFile(wb, name + ".xlsx");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
button {
  width: 200px;
  height: 40px;
  line-height: 40px;
  cursor: pointer;
  background: blue;
  color: #ffffff;
}
</style>
