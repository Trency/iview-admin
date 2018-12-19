<template>
  <div>
    <Card>
      <div style="margin: 10px 0">
        产品名称：
        <Input placeholder="" style="width: auto; margin: 0 10px" />
        贷款金额：
        <Input placeholder="" style="width: auto; margin: 0 10px" />
        上架状态：
        <Select v-model="userStatus" style="width:200px">
          <Option v-for="item in userStatusList" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
        <Button type="primary" @click="searchUser" stype="margin: 0 10px">查询</Button>
        <Button @click="clearSearchText" style="margin: 0 10px">重置</Button>
      </div>
      <tables ref="tables" v-model="tableData" :columns="columns" @on-delete="handleDelete"/>
    </Card>
  </div>
</template>

<script>
  import Tables from '_c/tables'
  import { getFeaturedPage, getTableData } from '@/api/data'

  export default {
    name: 'user_manager',
    components: {
      Tables
    },
    data () {
      return {
        columns: [
          {title: 'Name', key: 'name', sortable: true},
          {title: 'Email', key: 'email', editable: true},
          {title: 'Create-Time', key: 'createTime'},
          {
            title: 'Handle',
            key: 'handle',
            options: ['delete'],
            button: [
              (h, params, vm) => {
                return h('Poptip', {
                  props: {
                    confirm: true,
                    title: '你确定要删除吗?'
                  },
                  on: {
                    'on-ok': () => {
                      vm.$emit('on-delete', params)
                      vm.$emit('input', params.tableData.filter((item, index) => index !== params.row.initRowIndex))
                    }
                  }
                }, [
                  h('Button', '自定义删除')
                ])
              }
            ]
          }
        ],
        tableData: [],
        infoStatusList: [
          {
            'value': 'pre_check',
            'label': '审核中'
          },
          {
            'value': 'checkedzzz',
            'label': '已审核'
          }
        ],
        infoStatus: '',
        userStatusList: [
          {
            'value': 'checked1',
            'label': '1'
          },
          {
            'value': 'checked2',
            'label': '2'
          },
          {
            'value': 'checked3',
            'label': '3'
          },
        ],
        userStatus: ''
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
