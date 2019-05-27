<template>
  <div class="about">
    <h1>This is an about page</h1>
    <export-excel :type="1" />
  </div>
</template>
<script>
import ExportExcel from '../components/ExportExcel'
export default {
  components: {
    ExportExcel
  }
}
</script>
