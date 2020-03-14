<template>
  <div class="loginbox">
    <div class="box">
      <el-form ref="loginform" :model="form" label-width="80px">
        <el-form-item>
          <el-input v-model="form.mobile" placeholder="请输入手机号" id="mobile"></el-input>
        </el-form-item>
        <el-form-item>
          <el-input v-model="form.code" placeholder="验证码"></el-input>
        </el-form-item>
        <el-from-item style="text-align:left">
          <el-checkbox v-model="form.xieyi" style="margin-right:10px">我已经阅读并同意和隐私条款协议</el-checkbox>
        </el-from-item>
        <el-from-item>
          <el-button style="width:100%" @click="login">登录</el-button>
        </el-from-item>
      </el-form>
    </div>
  </div>
</template>
 
<script>
export default {
  name: "login",
  data() {
    return {
      form: {
        mobile: "15366501228",
        code: "246810",
        xieyi: true
      }
    };
  },
  methods: {
    async login() {
      const res = await this.$http.post("authorizations", this.form);
     console.log(res)
     window.sessionStorage.setItem('user',JSON.stringify(res.data.data))
     this.$router.push("/home");
    }
  },
  created() {
    // console.log(this.$http);
  }
};
</script>
<style scoped lang = "less">
.loginbox {
  background-color: gray;
  display: flex;
  height: 100%;
  justify-content: center;
  align-items: center;
  .box {
    width: 400px;
    height: 340px;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    .el-form {
      width: 85%;
    }
    .el-input {
      width: 100%;
    }
  }
}
</style>