<template>
  <Card>
    <Form :model="formItem" :label-width="120">
      <Card title="基本信息">
        <Row>
          <Col span="6">
            <FormItem label="产品名称">
              <p>xxx</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="贷款金额">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="贷款天数">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="利率">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="利息金额">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="违约金类型">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="违约金利率">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="允许延长天数">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="标题">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="子标题">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="12">
            <FormItem label="产品描述">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="封面图">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
      </Card>

      <FormItem>
        <Button style="margin-left: 6px">取消</Button>
      </FormItem>
    </Form>
  </Card>
</template>
<script>
import Tables from '_c/tables'
import { getTableData, getFeaturedPage } from '@/api/data'
export default {
  name: "product_detail_page",
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
      }
    };
  }
};
</script>

