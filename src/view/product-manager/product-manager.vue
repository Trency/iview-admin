<template>
  <div>
    <Card>
      <Form ref="formValidate" :model="formValidate" :label-width="60" inline>
        <FormItem label="产品名称" prop="name">
          <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
        </FormItem>
        <FormItem label="贷款金额" prop="mail">
          <Input v-model="formValidate.mail" placeholder style="width: 130px"></Input>
        </FormItem>
        <FormItem label="借款天数" prop="city">
          <Input v-model="formValidate.mail" placeholder style="width: 130px"></Input>
        </FormItem>
        <FormItem label="产品状态" prop="interest">
          <Select v-model="formValidate.city" placeholder style="width: 130px">
            <Option value="beijing">New York</Option>
            <Option value="shanghai">London</Option>
            <Option value="shenzhen">Sydney</Option>
          </Select>
        </FormItem>
        <FormItem>
          <Button type="primary">搜索</Button>
          <Button style="margin-left: 8px">重置</Button>
        </FormItem>
        <Button type="primary" style="float: right" @click="add">新增</Button>
      </Form>
          
      
      <Table border :columns="columns12" :data="data6">
        <template slot-scope="{ row, index }" slot="action">
          <Button type="primary" size="small" style="margin-right: 5px" @click="show(index)">查看</Button>
          <Button type="error" size="small" @click="changeStatus(index)">下架</Button>
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
            :page-size="20"
          ></Page>
        </div>
      </div>
    </Card>
  </div>
</template>

<script>
import Tables from "_c/tables";
import { getTableData, getFeaturedPage } from "@/api/data";
export default {
  name: "product_manager_page",
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
          width: 40,
          align: "center"
        },
        {
          title: "产品名称",
          key: "name"
        },
        {
          title: "贷款金额",
          key: "age"
        },
        {
          title: "借款天数",
          key: "age"
        },
        {
          title: "利息金额",
          key: "address"
        },
        {
          title: "利率",
          key: "address"
        },
        {
          title: "违约金利率",
          key: "address"
        },
        {
          title: "违约金类型",
          key: "address"
        },
          {
          title: "库存",
          key: "address"
        },
        {
          title: "产品状态",
          key: "address"
        },
        {
          title: "操作",
          slot: "action",
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
      tableData: []
    };
  },
  methods: {
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
    },
    show(index) {
      this.$router.push({ name: "product_detail_page" });
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
    add() {
      this.$router.push({ name: "product_add_page" });
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
