<template>
  <div class="login_container">
    <div class="login_box">
      <div class="avatar_box">
        <img src="../assets/logo.png" width="130px" height="130px" style="border-radius: 50%; background-color: cornsilk">
      </div>
      <el-form :model="loginForm" :rules="loginFormRules" class="login_form" ref="loginFormRef">
        <el-form-item prop="username">
          <el-input v-model="loginForm.username" prefix-icon="el-icon-user-solid" ></el-input>
        </el-form-item>

        <el-form-item prop="password">
          <el-input v-model="loginForm.password" type="password" prefix-icon="el-icon-lock"></el-input>
        </el-form-item>

        <el-form-item class="btns">
          <el-button type="primary" @click="login">登录</el-button>
          <el-button type="info">重置</el-button>
        </el-form-item>
      </el-form>


    </div>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        loginForm:{
          username:'',
          password:''
        },
        loginFormRules:{
          username:[
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
          ],
          password:[
            { required: true, message: '请输入密码', trigger: 'blur' },
            { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
          ]
        }
      }
    },
    methods:{
      login(){
        this.$refs.loginFormRef.validate(valid =>{
          // console.log(valid);
          if(!valid) return;
          // const result = this.$http.post('login', this.loginFrom);
          // console.log(result);
          if(this.loginForm.username=="admin" && this.loginForm.password=="123456"){
            //console.log("yes");
            this.$message.success('登陆成功');
            this.$router.push('/home');
          }
          else{
            // console.log("no");
            return this.$message.error('登录失败');
            console.log(this.loginForm.username);
            console.log(this.loginForm.password);
          }
        })
      }
    }
  }
</script>

<style scoped>
  .login_container{
    background-color: cornflowerblue;
    height: 100%;
  }

  .login_box{
    width:450px;
    height: 300px;
    background-color: white;
    border-radius: 3px;
    position: absolute;
    left: 50%;
    top:50%;
    transform: translate(-50%, -50%);
  }

  .avatar_box{
    width: 130px;
    height: 130px;
     border: 1px solid cornsilk;
    border-radius: 50%;
    padding: 10px;
    box-shadow: 0 0 10px #eeeeee;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #eeeeee;
  }

  .login_form{
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 0 20px;
    box-sizing: border-box;
  }
  .btns{
    display: flex;
    justify-content: center;
  }
</style>
