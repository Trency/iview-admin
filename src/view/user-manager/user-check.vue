<template>    <Form :model="formItem" :label-width="120">
      <Card title="个人信息资料">
        <Row>
          <Col span="6">
            <FormItem label="姓名">
              <p>xxx</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="手机号">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="身份证号">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="注册来源">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="学校">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="学号">
              <p>aaa</p>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="公司">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="最后登录时间">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="状态">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="6">
            <FormItem label="最后登录IP">
              <p>aaa</p>
            </FormItem>
          </Col>
          <Col span="12">
            <FormItem label="现居地址">
              <p>aaa</p>
            </FormItem>
          </Col>
        </Row>
      </Card>

      <Card title="个人身份认证">
        <Row>
          <Col span="8">
            <FormItem label="身份证正面照">
              <img
                src="http://jumax-store-latest.oss-cn-shanghai.aliyuncs.com/uploading/2018-12-11/20181211203439547.jpg"
                height="200px"
              >
            </FormItem>
          </Col>

          <Col span="8">
            <FormItem label="身份证背面照">
              <img
                src="http://jumax-store-latest.oss-cn-shanghai.aliyuncs.com/uploading/2018-12-11/20181211203519058.JPG"
                height="200px"
              >
            </FormItem>
          </Col>
        </Row>
      </Card>

      <Card title="扫脸认证">
        <Row>
          <Col span="8">
            <FormItem label="扫脸认证信息">
              <img
                src="https://www.xiazaiba.com/uploadfiles/content/2014/0905/water_140990556072090231552.jpg"
                height="200px"
              >
            </FormItem>
          </Col>
        </Row>
      </Card>

      <Card title="联系人证明信息">
        <Row>
          <Col span="12">
            <Table border :columns="columns12" :data="data6"></Table>
          </Col>
        </Row>
      </Card>

      <Card title="绑定账号">
        <Row>
          <Col span="8">
            <FormItem label="支付宝账号">
              <p>mayun@ali.com</p>
            </FormItem>
          </Col>
        </Row>
      </Card>

      <Card title="审核">
        <Row>
          <Col span="6">
            <FormItem label="信息状态">
              <RadioGroup>
                <Radio label="暂不处理"></Radio>
                <Radio label="通过"></Radio>
                <Radio label="拒绝"></Radio>
              </RadioGroup>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="身份证状态">
              <RadioGroup>
                <Radio label="暂不处理"></Radio>
                <Radio label="通过"></Radio>
                <Radio label="拒绝"></Radio>
              </RadioGroup>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="扫脸状态">
              <RadioGroup>
                <Radio label="暂不处理"></Radio>
                <Radio label="通过"></Radio>
                <Radio label="拒绝"></Radio>
              </RadioGroup>
            </FormItem>
          </Col>
        </Row>
        <Row>
          <Col span="6">
            <FormItem label="联系人状态">
              <RadioGroup>
                <Radio label="暂不处理"></Radio>
                <Radio label="通过"></Radio>
                <Radio label="拒绝"></Radio>
              </RadioGroup>
            </FormItem>
          </Col>

          <Col span="6">
            <FormItem label="绑定账号状态">
              <RadioGroup>
                <Radio label="暂不处理"></Radio>
                <Radio label="通过"></Radio>
                <Radio label="拒绝"></Radio>
              </RadioGroup>
            </FormItem>
          </Col>
        </Row>
      </Card>

      <div style="float: right; margin: 10px 0">
    <Button type="primary">保存</Button>
    <Button style="margin-left: 6px">取消</Button>
    </div>
    </Form>
    
</template>
<script>
export default {
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
      columns12: [
        {
          type: "index",
          width: 40,
          align: "center"
        },
        {
          title: "姓名",
          key: "name"
        },
        {
          title: "亲属关系",
          key: "age"
        },
        {
          title: "联系电话",
          key: "address"
        }
      ]
    };
  }
};
</script>
