<template>
  <div>
    <!-- <Card> -->
      <!-- <Card> -->

      <Form ref="formValidate" :model="formValidate" :label-width="60" inline>
        <FormItem label="姓名" prop="name">
          <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
        </FormItem>
        <FormItem label="手机号" prop="mail">
          <Input v-model="formValidate.mail" placeholder style="width: 130px"></Input>
        </FormItem>
        <FormItem label="用户状态" prop="city">
          <Select v-model="formValidate.city" placeholder style="width: 130px">
            <Option value="beijing">New York</Option>
            <Option value="shanghai">London</Option>
            <Option value="shenzhen">Sydney</Option>
          </Select>
        </FormItem>
        <FormItem label="审核状态" prop="interest">
          <Select v-model="formValidate.city" placeholder style="width: 130px">
            <Option value="beijing">New York</Option>
            <Option value="shanghai">London</Option>
            <Option value="shenzhen">Sydney</Option>
          </Select>
        </FormItem>
        <FormItem>
          <Button type="primary" @click="search">搜索</Button>
          <Button style="margin-left: 8px">重置</Button>
        </FormItem>
      </Form>
    <!-- </Card> -->

      <Table border :columns="columns12" :data="tableData">
        <template slot-scope="{ row, index }" slot="action">
          <Button type="primary" size="small" style="margin-right: 5px" @click="show(index)">查看</Button>
          <Button type="error" size="small" @click="changeStatus(index)">禁用</Button>
        </template>
      </Table>
      <div style="margin: 10px 10px 0 10px;overflow: hidden">
        <div style="float: right; margin: 10px 0">
          <Page
            :total="100"
            :current="1"
            size="small"
            show-elevator
            show-sizer
            show-total
            :page-size="25"
            on-page-size-change="changeZZZ"
          ></Page>
        </div>
      </div>
    <!-- </Card> -->
  </div>
</template>

<script>
import Tables from "_c/tables";
import { getTableData, getFeaturedPage } from "@/api/data";
export default {
  name: "user_manager",
  components: {
    Tables
  },
  data() {
    return {
      formValidate: {
        name: "",
        mail: "",
        city: "",
        gender: "",
        interest: [],
        date: "",
        time: "",
        desc: ""
      },

      columns12: [
        {
          type: "index",
          width: 60,
          align: "center"
        },
        {
          title: "姓名",
          key: "name"
        },
        {
          title: "手机号",
          key: "age"
        },
        {
          title: "身份证号",
          key: "address"
        },
        {
          title: "用户状态",
          key: "address"
        },
        {
          title: "信息状态",
          key: "address"
        },
        {
          title: "注册时间",
          key: "address"
        },
        {
          title: "操作",
          slot: "action",
          align: "center"
        }
      ],
      tableData: []
    };
  },
  methods: {
    handleDelete(params) {
      console.log(params);
    },
    exportExcel() {
      this.$refs.tables.exportCsv({
        filename: `table-${new Date().valueOf()}.csv`
      });
    },
    search() {
      console.log(this.tableData.length)
    },
    clearSearchText() {
      this.userStatus = "";
      this.infoStatus = "";
    },
    show(index) {
      this.$router.push({ name: "user_check_page" });
    },
    changeStatus(index) {
      this.$Modal.confirm({
        title: "确认要禁用该用户吗",
        content: "禁用用户后，将无法进行登录或借还款操作",
        onOk: () => {
          this.$Message.info("禁用成功");
        }
      });
    },
    changeZZZ(param) {
      console.log('123')
      console.log(param)
    }
  },
  mounted() {
    getTableData().then(res => {
      this.tableData = res.data;
    });
  }
};
</script>

<style>
</style>
