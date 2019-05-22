<template>
  <div class="export-excel-wrap">
    <button
      id="export-btn"
      @click="exportExcel"
    >导出表格</button>
    <table id="export-table">
      <thead>
        <tr>
          <td>序号</td>
          <td>产地</td>
          <td>数量</td>
          <td>价格</td>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>北京</td>
          <td>3633</td>
          <td>156</td>
        </tr>
        <tr>
          <td>2</td>
          <td>上海</td>
          <td>3633</td>
          <td>156</td>
        </tr>
        <tr>
          <td t="s">003</td>
          <td>重庆</td>
          <td>3633</td>
          <td>156</td>
        </tr>
        <tr>
          <td>4</td>
          <td>天津</td>
          <td>3633</td>
          <td>156</td>
        </tr>
        <tr>
          <td>5</td>
          <td>广州</td>
          <td>3633</td>
          <td>15611</td>
        </tr>
        <tr>
          <td>8</td>
          <td>深圳</td>
          <td>3633</td>
          <td>15632</td>
        </tr>
        <tr>
          <td>9</td>
          <td>杭州</td>
          <td>3633</td>
          <td>15688</td>
        </tr>
        <tr>
          <td>10</td>
          <td>成都</td>
          <td>3633</td>
          <td>15600</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import XLSX from 'xlsx'
/* var obj = {
  cols: [{ name: 'A', key: 0 }, { name: 'B', key: 1 }, { name: 'C', key: 2 }],
  data: [['id', 'name', 'value'], [1, 'sheetjs', 7262], [2, 'js-xlsx', 6969]]
} */
export default {
  props: {},
  components: {},
  data() {
    return {}
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    multipleTable() {
      /* create new workbook */
      var workbook = XLSX.utils.book_new()

      /* convert table 'table1' to worksheet named "Sheet1" */
      var ws1 = XLSX.utils.table_to_sheet(document.getElementById('table1'))
      XLSX.utils.book_append_sheet(workbook, ws1, 'Sheet1')

      /* convert table 'table2' to worksheet named "Sheet2" */
      var ws2 = XLSX.utils.table_to_sheet(document.getElementById('table2'))
      XLSX.utils.book_append_sheet(workbook, ws2, 'Sheet2')
      XLSX.writeFile(workbook, 'out2.xlsx')
    },
    exportExcel() {
      /* var worksheet = XLSX.utils.aoa_to_sheet(obj)
      var newWorkbook = XLSX.utils.book_new() */
      var table = document.getElementById('export-table')
      var wb = XLSX.utils.table_to_book(table)
      // XLSX.utils.book_append_sheet(newWorkbook, worksheet, 'SheetJS')
      XLSX.writeFile(wb, 'out.xlsx')
    }
  }
}
</script>

<style scoped lang="scss">
</style>
