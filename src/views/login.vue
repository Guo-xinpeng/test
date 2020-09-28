<template>
  <div class="box">
    <div class="login">
      <el-input v-model="username" placeholder="请输入用户名"></el-input>
      <el-input v-model="password" placeholder="请输入密码" type="password"></el-input>
      <el-button type="primary" @click="login">登录</el-button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  mounted() {},
  methods: {
    // 请求
    login() {
      this.$axios
        .post("https://www.liulongbin.top:8888/api/private/v1/login", {
          username: this.username,
          password: this.password,
        })
        .then((res) => {
          console.log(res);

          this.$message({
            type: "info",
            message: res.data.meta.msg,
          });
          
          if (res.data.meta.status === 200) {
            localStorage.TOKEN = res.data.data.token;
            setTimeout(() => {
              this.$router.push({
                  path:'/about'
              })
            }, 1000);
          }
        });
    },
  },
};
</script>

<style>
.box {
  width: 100%;
  height: 100vh;
}
.login {
  width: 25%;
  height: 39%;
  padding: 10px;
  background: #fff;
  display: flex;
  flex-direction: column;
  position: fixed;
  top: 30%;
  left: 34%;
  border: 1px black solid;
}
.el-input {
  margin: 20px 0;
}
</style>