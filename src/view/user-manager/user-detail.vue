<template>
  <div>
    <Card>
    <Row :gutter="16">
        <Col span="6">
        </Col>
        <Col span="6">
        </Col>
        <Col span="6">
        </Col>
        <Col span="6">
        </Col>
    </Row>
    </Card>
  </div>
</template>

<script>
import Tables from '_c/tables'
import { getTableData, getFeaturedPage } from '@/api/data'
export default {
  name: 'user_manager',
  components: {
    Tables
  },
  data () {
    return {
      
    }
  },
  methods: {
    handleDelete (params) {
      console.log(params)
    },
    exportExcel () {
      this.$refs.tables.exportCsv({
        filename: `table-${(new Date()).valueOf()}.csv`
      })
    },
    searchUser () {
        console.log(this.userStatus)
        console.log(this.infoStatus)
        getTableData().then(res => {
            this.tableData = res.data
            console.log('123')
        })
    },
    clearSearchText () {
        this.userStatus = ''
        this.infoStatus = ''
    }
  },
  mounted () {
    getTableData().then(res => {
      this.tableData = res.data
    })
  }
}
</script>

<style>

</style>
