<template>
  <div class="login_container">
    <div class="login_box">
<!--      头像区域-->
      <div class="avatar_box">
        <img src="@/assets/logo.png" alt="">
      </div>
<!--      表单-->
      <el-form ref="loginDataRef" :model="loginData" :rules="rules" class="login_form">
        <el-form-item prop="username">
          <el-input v-model="loginData.username" prefix-icon="el-icon-user"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input type="password" v-model="loginData.password" prefix-icon="el-icon-user"></el-input>
        </el-form-item>
        <el-form-item class="btns">
          <el-button type="primary" @click="submit('loginDataRef')">登陆</el-button>
          <el-button type="info" @click="reset('loginDataRef')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'login',
  methods: {
    reset (formRef) {
      this.$refs.loginDataRef.resetFields()
    },
    submit (formRef) {
      this.$refs.loginDataRef.validate(valid => {
        if (valid) {
          this.$http.get()
          alert('success')
        } else {
          console.log('error')
          return false
        }
      })
    }
  },
  data () {
    return {
      loginData: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
        ]
      }
    }
  }
}
</script>

<style lang="less" scoped>
  .login_container{
    background-color: #2b4b6b;
    height: 100%;
    .login_box{
      width: 450px;
      height: 300px;
      border-radius: 3px;
      background-color: #fff;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    .avatar_box{
      width: 130px;
      height: 130px;
      border: 1px solid #eee;
      border-radius: 50%;
      padding: 10px;
      box-shadow: 0 0 10px #ddd;
      position: absolute;
      left: 50%;
      top: 0;
      transform: translate(-50%, -50%);
      background-color: #fff;
      img {
        height: 100%;
        width: 100%;
        border-radius: 50%;
        background-color: #eeeeee;
      }
    }
  }
  .btns{
    display: flex;
    justify-content: flex-end;
  }
  .login_form{
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 0 10px;
    box-sizing: border-box;
  }
</style>
