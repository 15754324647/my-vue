<template>
  <div>
    <!--    <label>-->
    <!--      用户名称：<input type="text" v-model="userName" aria-placeholder="请输入用户名"/>-->
    <!--    </label>-->
    <label>用户姓名：
      <el-input v-model="realName" placeholder="请输入姓名" size="medium"></el-input>
    </label>
    <label>用户昵称：
      <el-input v-model="nick" placeholder="请输入昵称" size="medium"></el-input>
    </label>
    <el-button type="primary" @click="register()">注册</el-button>
  </div>

</template>

<script>
  export default {
    name: "Registration",
    data() {
      return {
        realName: "",
        nick: ""
      }
    },
    methods: {
      register() {
        console.log(this.realName)
        console.log(this.nick)
      }
    }
  }
</script>

<style scoped>
  .el-input {
    width: 10%;
  }
</style>
