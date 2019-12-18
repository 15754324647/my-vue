<template>
  <div>
    <label>用户名称：
      <el-input v-model="userName" placeholder="请输入名称" size="large"></el-input>
    </label>
    <label>用户姓名：
      <el-input v-model="realName" placeholder="请输入姓名" size="medium"></el-input>
    </label>
    <label>用户昵称：
      <el-input v-model="nick" placeholder="请输入昵称" size="small"></el-input>
    </label>
    <label>用户密码：
      <el-input v-model="password" placeholder="请输入密码" size="small"></el-input>
    </label>
    <label>用户手机号：
      <el-input v-model="mobile" placeholder="请输入手机号" size="small"></el-input>
    </label>
    <el-button type="primary" @click="sendUserInfo()">注册</el-button>
  </div>

</template>

<script>
  export default {
    name: "Registration",
    data() {
      return {
        userName: '',
        realName: "",
        nick: "",
        password: "",
        mobile: ""

      }
    },
    methods: {
      register() {
        console.log(this.realName)
        console.log(this.nick)
      },
      sendUserInfo() {
        this.$http.post('user/insert', {
          userName: this.userName,
          realName: this.realName,
          nick: this.nick,
          password: this.password,
          mobile: this.mobile
        }).then(response => {
          if (response) {
            console.log(response);
          }
        }).catch(error => {
          console.log(error);
        })
      }
    }
  }
</script>

<style scoped>
  .el-input {
    width: 10%;
  }
</style>
