<template>
  <el-container>
    <el-header class="header">
      <vheader />
    </el-header>

    <el-header>
      <div class="header-left">
        <img src='../image/logo.jpg'>
      </div>
      <div class="header-right">
        <span class="huan-login">欢迎登录</span>
      </div>
    </el-header>
    <!--<hr style="width:100%;border: 1px solid black;margin-top: 30px"/>-->
    <div style="width:100%;border-top: 1px solid  #CCCCCC;transform: scaleY(1);margin-top: 50px"></div>

    <div class="main-background">
    <el-main>
      <div class="main-right">
        <div class="login-outside">
          <div class="login-right-reg">
            <span class="user-login-word">用户登录</span>
          </div>
          <hr style="color:#c5c4c4;margin-bottom: 5px;border-width: 1px 0px 0px;border-top-width: 1px;border-top-style: solid;padding-bottom: 10px;">

          <div class="login-form-style">

            <!--登陆form表单-->
            <el-form autoComplete="on" :model="loginForm" :rules="loginRules" ref="loginForm" label-position="left" label-width="0px"
                     class="card-box login-form">
              <!--<h3 class="title">vue-element-admin</h3>-->
              <el-form-item prop="username">
                <span class="svg-container svg-container_login">
                  <svg-icon icon-class="user" />
                </span>
                <el-input name="username" type="text" v-model="loginForm.username" autoComplete="on" placeholder="username" />
              </el-form-item>

              <el-form-item prop="password">
                <span class="svg-container">
                  <svg-icon icon-class="password"></svg-icon>
                </span>
                <!--@keyup.enter.native:按回车触发登陆 autoComplete:启用自动完成功能   placeholder:文本框注释-->
                <el-input name="password" :type="pwdType" @keyup.enter.native="handleLogin" v-model="loginForm.password" autoComplete="on"
                          placeholder="password"></el-input>
                <!--所有的v-on都可以简写为@，比如说v-click可以简写为@click  单击触发事件-->
                <span class="show-pwd" @click="showPwd"><svg-icon icon-class="eye" /></span>
              </el-form-item>
                <!--@click.native.prevent="handleLogin"：单击 键盘事件要加native，阻止冒泡-->
                <el-button type="primary" style="width:100%;"  @click.native.prevent="handleLogin">
                  登录
                </el-button>
            </el-form>
            <div class="no-user">
                还没有账号？<router-link to="/register"><a href="Register.vue">立即注册</a></router-link>
              </div>
            <div>

            </div>
          </div>
        </div>
      </div>

    </el-main>
    </div>
  </el-container>
</template>

<script>
  import Header from '@/components/Header'
  // import request from '@/utils/request'
  export default {
    components: {
      'vheader': Header
    },
    data(){
      const validateUsername = (rule, value, callback) => {
      // if (value.length = 0) {
      //   callback(new Error('请输入用户名'))
      // } else {
      //   callback()
      // }
    }
      const validatePass = (rule, value, callback) => {
        if (value.length < 5) {
          callback(new Error('密码不能小于5位'))
        } else {
          callback()
        }
      }
      return {
        loginForm: {
          username: '',
          password: ''
        },
        loginRules: {
          username: [{ required: true, trigger: 'blur', validator: validateUsername }],
          password: [{ required: true, trigger: 'blur', validator: validatePass }]
        },
        loading: false,
        pwdType: 'password'
      }
    },
    methods: {
      showPwd() {
        if (this.pwdType === 'password') {
          this.pwdType = ''
        } else {
          this.pwdType = 'password'
        }
      },

      handleLogin() {
        debugger
        // this.$refs.loginForm.validate(valid => {
          // if (valid) {
          //   this.loading = true
          //   this.$axios.post('/user/login'+'?username='+this.loginForm.username+'&password='+this.loginForm.password).then((response) =>{
          //   }
          //     debugger
          //     this.$store.dispatch('login', this.user).then(() => {
          //       // this.$notify({
          //       //   type: 'success',
          //       //   // message: '欢迎你,' + this.user.name + '!',
          //       //   duration: 3000
          //       // })
          //       this.$router.replace('/')
          //     })
          //   }).catch((error) =>{
          //     console.log(error)
          //   })
          // if (valid) {
            if (this.loginForm.username === 'admin' && this.loginForm.password === 'admin') {
              // dispatch采用Promise链式调用
              this.$store.dispatch('login', this.loginForm.username).then(() => {
                // this.$notify({
                //   type: 'success',
                //   message: '欢迎你,' + this.user.name + '!',
                //   duration: 3000
                // })
                this.$router.replace('/')
              })
            }
          // } else {
          //   return false
          // }
        // })
      }

    }
    }

</script>

<style rel="stylesheet/scss" lang="scss">
  $bg:#2d3a4b;
  $dark_gray:#889aa4;
  $light_gray:#eee;

  .header-left{
    margin-left: 350px;
    float: left;
  }
  .header-right{
    width: 200px;
    height: 35px;
    border-left: 1px solid #cecdcd;
    margin-left: 50px;
    margin-top: 24px;
    float: left;
  }
  .huan-login{
    margin-left: 20px;
    line-height: 35px;
    font-size: 25px;
    font-family: '黑体';
    color: #979997;
  }
  .main-background{
    width: 100%;
    height: 748px;
    background: url("../image/background1.jpg") no-repeat;
  }
  .aside-img{
    float: left;
  }
  .main-right{
    width: 417px;
    height: 380px;
    border: 1px solid #d7d7d7;
    border-top: 2px solid red;
    margin-top: 120px;
    margin-left: 1150px;
    float: left;
  }
  .login-outside{
    width: 335px;
    height: 330px;
    /*border: 1px solid black;*/
    margin-top: 41px;
    margin-left: 44px;
  }
  .user-login-word{
    font-size: 24px;
    color: #7a7a7a;
  }
  .login-form-style{
    width: 335px;
    height: 284px;
    /*border: 1px solid black;*/
    input:-webkit-autofill {
      /*-webkit-box-shadow: 0 0 0px 1000px #293444 inset !important;*/
      -webkit-text-fill-color: #fff !important;
    }
    input {
      background: transparent;
      border: 0px;
      -webkit-appearance: none;
      border-radius: 0px;
      padding: 12px 5px 12px 15px;
      color: $light_gray;
      height: 47px;
    }
    .el-input {
      display: inline-block;
      height: 47px;
      width: 80%;
    }
    .tips {
      font-size: 14px;
      color: #fff;
      margin-bottom: 10px;
    }
    .svg-container {
      padding: 6px 5px 6px 15px;
      color: $dark_gray;
      vertical-align: middle;
      width: 30px;
      display: inline-block;
      &_login {
        font-size: 20px;
      }
    }
    .title {
      font-size: 26px;
      font-weight: 400;
      color: $light_gray;
      margin: 0px auto 40px auto;
      text-align: center;
      font-weight: bold;
    }
    /*.login-form {*/
      /*position: absolute;*/
      /*left: 0;*/
      /*right: 0;*/
      /*width: 400px;*/
      /*padding: 35px 35px 15px 35px;*/
      /*margin: 120px auto;*/
    /*}*/
    .el-form-item {
      border: 1px solid rgba(255, 255, 255, 0.1);
      /*background: rgba(0, 0, 0, 0.1);*/
      /*border-radius: 5px;*/
      border-color: #c5c4c4;
      /*color: #454545;*/
    }
    .el-input__inner{
      width: 100%;
      height: 40px;
      font-size: 18px;
      color: #979997;
    }
    .show-pwd {
      position: absolute;
      right: 10px;
      top: 7px;
      font-size: 16px;
      color: $dark_gray;
      cursor: pointer;
      user-select:none;
    }
    .thirdparty-button{
      position: absolute;
      right: 35px;
      bottom: 28px;
    }
    .el-button--primary {
      color: #FFF;
      background-color: red;
      border-color: red;
    }
    .no-user{
      margin-top: 20px;
      color: #535252;
    }
    a:link{
      color: #3f5aa7;
    }
  }


  /*form表单*/


</style>
