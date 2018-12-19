<template>
  <Card>
    <Form :model="formItem" :label-width="120">
      <Card title="基本信息">
        <Row>
          <Col span="6">
            <FormItem label="产品名称">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="贷款金额">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="贷款天数">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="利率">
             <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="利息金额">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="违约金类型">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="违约金利率">
             <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="允许延长天数">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="标题">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="子标题">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
          <Col span="12">
            <FormItem label="产品描述">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="封面图">
              <Input v-model="formValidate.name" placeholder="请输入用户姓名" style="width: 130px"></Input>
            </FormItem>
          </Col>
        </Row>
      </Card>

      <FormItem>
        <Button type="primary">保存</Button>
        <Button style="margin-left: 6px">取消</Button>
      </FormItem>
    </Form>
  </Card>
</template>
<script>
import Tables from '_c/tables'
import { getTableData, getFeaturedPage } from '@/api/data'
export default {
  name: "product_add_page",
  components: {
    Tables
  },
  data() {
    return {
      formItem: {
        input: "李四",
        select: "",
        radio: "male",
        checkbox: [],
        switch: true,
        date: "",
        time: "",
        slider: [20, 50],
        textarea: ""
      },
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
    };
  }
};
</script>
