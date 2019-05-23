<template>
  <div class="export-excel-wrap">
    <button
      id="export-btn"
      @click="exportExcel"
    >导出表格</button>
    <button
      id="export-btn2"
      @click="exportJson"
    >导出数据</button>
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
  props: {
    type: { // 表格类型 1: 从表格导出 2: 从json对象导出
      type: Number,
      required: true
    },
    thead: {
      type: Object,
      default: () => ({})
    },
    tbody: {
      type: Array,
      default: () => []
    }
  },
  components: {},
  data () {
    return {}
  },
  computed: {},
  created () {},
  mounted () {},
  watch: {},
  methods: {
    multipleTable () {
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
    exportJson () {
      var ws = XLSX.utils.json_to_sheet([
        { S: 1, h: 2, e: 3, e_1: 4, t: 5, J: 6, S_1: 7 },
        { S: 2, h: 3, e: 4, e_1: 5, t: 6, J: 7, S_1: 8 }
      ], { header: ['S', 'h', 'e', 'e_1', 't', 'J', 'S_1'] })
      var ws2 = XLSX.utils.json_to_sheet([
        { A: 'S', B: 'h', C: 'e', D: 'e', E: 't', F: 'J', G: 'S' },
        { A: 1, B: 2, C: 3, D: 4, E: 5, F: 6, G: 7 },
        { A: 2, B: 3, C: 4, D: 5, E: 6, F: 7, G: 8 }
      ], { header: ['A', 'B', 'C', 'D', 'E', 'F', 'G'], skipHeader: true })
      var wb = XLSX.utils.book_new()
      XLSX.utils.book_append_sheet(wb, ws, '表格1')
      XLSX.utils.book_append_sheet(wb, ws2, '表格2')
      XLSX.writeFile(wb, 'json.xlsx')
    },
    exportExcel () {
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
.export-excel-wrap{
  button + button{
    margin-left: 10px;
  }
}
</style>
