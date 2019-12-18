<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="reverseMessage">点击小李</button>
    <button v-on:click="getUserInfo()">点击获取用户信息</button>
    <h2>{{userName}}</h2>
    <h2>{{realName}}</h2>
    <h2>{{nick}}</h2>
    <h2>{{mobile}}</h2>
    <!-- 通过自定义属性传数据-->
    <Child child="没错我就是child之一来学习props的单向绑定，由爸爸到儿子"></Child>
    <Registration></Registration>
  </div>
</template>

<script>
  import Registration from '../components/Registration'
  import Child from '../components/Child'

  export default {
    components: {Registration,Child},
    name: 'HelloWorld',
    data() {
      return {
        msg: "Welcome to Your Vue.js App",
        xiao: "小李来测试2.0",
        index: "小李的xiaowang ",
        userName: "我是userName",
        realName: "我是realName",
        nick: "我是nick",
        mobile: "我是mobile",
        userList: []
      }
    },
    methods: {
      //翻转字符串
      reverseMessage: function () {

        this.msg = this.msg.split("").reverse().join("");
      },
      getUserInfo() {
        this.userList = [];
        this.$http.get('/user/info').then(response => {
          this.userList = response.data[0];
          this.userName = this.userList.userName;
          this.realName = this.userList.realName;
          this.mobile = this.userList.mobile;
          // this.userName = response[0].userName;
          console.log(response)
        }).catch(function (error) {
          console.log(error)
        })
      },
      login(){
        console.log(this.userName);
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1,
  h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
