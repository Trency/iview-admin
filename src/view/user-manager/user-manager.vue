<template>
  <div>
    <Card>
      <Form ref="formValidate" :model="formValidate" :label-width="60" label-position="left" inline>
        <FormItem label="姓名" prop="name">
          <Input v-model="formValidate.name" placeholder="Enter your name"></Input>
        </FormItem>
        <FormItem label="手机号" prop="mail">
          <Input v-model="formValidate.mail" placeholder="Enter your e-mail"></Input>
        </FormItem>
        <FormItem label="用户状态" prop="city">
          <Select v-model="formValidate.city" placeholder="Select your city">
            <Option value="beijing">New York</Option>
            <Option value="shanghai">London</Option>
            <Option value="shenzhen">Sydney</Option>
          </Select>
        </FormItem>
        <FormItem label="审核状态" prop="interest">
          <Select v-model="formValidate.city" placeholder="Select your city">
            <Option value="beijing">New York</Option>
            <Option value="shanghai">London</Option>
            <Option value="shenzhen">Sydney</Option>
          </Select>
        </FormItem>
        <FormItem>
            <Button type="primary">Submit</Button>
            <Button style="margin-left: 8px">Cancel</Button>
        </FormItem>
      </Form>
      <Table border :columns="columns12" :data="data6">
        <template slot-scope="{ row }" slot="name">
          <strong>{{ row.name }}</strong>
        </template>
        <template slot-scope="{ row, index }" slot="action">
          <Button type="primary" size="small" style="margin-right: 5px">View</Button>
          <Button type="error" size="small">Delete</Button>
        </template>
      </Table>
      <div style="margin: 10px;overflow: hidden">
        <div style="float: right;">
          <Page :total="100" :current="1"></Page>
        </div>
      </div>
    </Card>
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
          title: "Name",
          slot: "name"
        },
        {
          title: "Age",
          key: "age"
        },
        {
          title: "Address",
          key: "address"
        },
        {
          title: "Action",
          slot: "action",
          width: 150,
          align: "center"
        }
      ],
      data6: [
        {
          name: "John Brown",
          age: 18,
          address: "New York No. 1 Lake Park"
        },
        {
          name: "Jim Green",
          age: 24,
          address: "London No. 1 Lake Park"
        },
        {
          name: "Joe Black",
          age: 30,
          address: "Sydney No. 1 Lake Park"
        },
        {
          name: "Jon Snow",
          age: 26,
          address: "Ottawa No. 2 Lake Park"
        }
      ],
      tableData: [],
      infoStatusList: [
        {
          value: "pre_check",
          label: "审核中"
        },
        {
          value: "checkedzzz",
          label: "已审核"
        }
      ],
      infoStatus: "",
      userStatusList: [
        {
          value: "checked1",
          label: "1"
        },
        {
          value: "checked2",
          label: "2"
        },
        {
          value: "checked3",
          label: "3"
        }
      ],
      userStatus: ""
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
    searchUser() {
      console.log(this.userStatus);
      console.log(this.infoStatus);
      getTableData().then(res => {
        this.tableData = res.data;
        console.log("123");
      });
    },
    clearSearchText() {
      this.userStatus = "";
      this.infoStatus = "";
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
