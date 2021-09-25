<!--  -->
<template>
  <div class="login_container">
    <div class="login_box">
      <!-- 头像 -->
      <div class="avatar_box">
        <img src="../assets/logo.png" alt="" />
      </div>
      <!-- 输入框 -->
        <el-form ref="loginFormRef" class="login_form" :model="loginForm" :rules="loginFormRules">
          <!-- 账号 -->
          <el-form-item prop="username">
            <el-input prefix-icon="el-icon-user" v-model="loginForm.username"></el-input>
          </el-form-item>
          <!-- 密码 -->
          <el-form-item prop="password">
            <el-input prefix-icon="el-icon-user-solid" v-model="loginForm.password" type="password"></el-input>
          </el-form-item>
          <!-- 按钮 -->
          <el-form-item class="btns">
            <el-button type="primary" round @click="login">登录</el-button>
            <el-button type="info" round @click="reset">重置</el-button>
          </el-form-item>
        </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        username: 'zs',
        password: '123'
      },
      // 验证规则
      loginFormRules: {
        username:
        [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 5, max: 15, message: '长度在 5 到 15 个字符', trigger: 'blur' }
        ],
        password:
        [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 5 到 15 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    reset () {
      this.$refs.loginFormRef.resetFields()
    },
    login () {
      this.$refs.loginFormRef.validate(async valid => {
        if(!valid)  return this.$message.error(("登陆失败"));
        this.$router.push('/home')
        // const {data: res} = await this.$http.post('',this.loginForm);
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_container {
  background-color: #2b4b6b;
  height: 100%;
}
.login_box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 3px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);

  .avatar_box {
    height: 130px;
    width: 130px;
    border: 1px solid #eee;
    border-radius: 50%;
    padding: 10px;
    box-shadow: 0 0 10px #ddd;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background-color: #eee;
    }
  }
}
.login_form {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
.btns {
  display: flex;
  justify-content: flex-end;
}
</style>
