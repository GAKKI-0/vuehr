<template>
  <div>
    <!-- v-bind: == : 表示表单内数据双向绑定 -->
    <!-- ref : 配上表单名字，通过定义的名字可以查找到表单 -->
    <el-form :rules="rules" ref="loginForm" :model="loginForm" class="loginContainer">
      <h3 class="loginTitle">系统登录</h3>
      <el-form-item prop="username">
        <!-- v-model 表示取值-->
        <el-input type="text" v-model="loginForm.username" auto-complete="off" placeholder="请输入用户名"></el-input>
      </el-form-item>
      <el-form-item prop="password">
        <el-input type="text" v-model="loginForm.password" auto-complete="off" placeholder="请输入密码"></el-input>
      </el-form-item>
      <!-- 是否记住密码 -->
      <el-checkbox v-model="checked" class="loginRemember"></el-checkbox>
      <!-- @click点击事件 -->
      <el-button type="primary" style="width: 100%;" @click="submitLogin">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      // 数据对象
      loginForm: {
        username: 'admin',
        password: 'admin'
      },
      // 表单验证
      rules: {
        username: [{required: true, message: '请输入用户名', trigger: 'blur'}],
        password: [{required: true, message: '请输入密码', trigger: 'blur'}]
      },
      checked: true
    }
  },
  methods: {
    submitLogin() {
      this.$refs.loginForm.validate((valid) => {
        if (valid) {
          alert("submit!");
        } else {
          // elementui 字段
          this.$message.error("请输入所有字段");
          return false;
        }
      });
    }
  }
}
</script>

<style scoped>
.loginContainer {
  border-radius: 15px;
  background-clip: padding-box;
  /*外边距*/
  margin: 180px auto;
  /*左右宽度*/
  width: 350px;
  /* 内边距*/
  padding: 25px 35px 25px 35px;
  /*背景*/
  background: #fff;
  /*边框*/
  border: 1px solid #eaeaea;
  /*阴影效果*/
  box-shadow: 0 0 25px #cac6c6;
}
.loginTitle {
  /* margin 外边距 上右下左*/
  margin: 15px auto 20px auto;
  /*文本对齐*/
  text-align: center;
  /*颜色*/
  color: #505458;
}

.loginRemember {
  text-align: left;
  margin: 0 0 15px 0;
}
</style>
