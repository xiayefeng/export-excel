<template>
  <div class="table-wrap">
    <table class="table">
      <thead>
        <tr>
          <th
            v-for="(item, name) in headObj"
            :key="name"
          >{{headObj[name]}}</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(item, idx) of tableData"
          :key="idx + (+new Date())"
          :class="{'heigh-line': idx % 2}"
          class="line"
        >
          <td
            v-for="(item2, name) in headObj"
            :key="name"
          >{{item[name]}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    headObj: {
      type: Object,
      required: true
    },
    tableData: {
      type: Array
    }
  },
  components: {

  },
  data () {
    return {

    }
  },
  computed: {

  },
  created () {

  },
  mounted () {

  },
  watch: {

  },
  methods: {

  }
}
</script>

<style scoped lang="scss">
</style>
