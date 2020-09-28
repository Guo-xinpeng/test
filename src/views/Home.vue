<template>
  <div>
    <div class="box">
      
     <el-container>
      <el-header>
        <h2>后台管理系统</h2>
        <el-button @click="dict">退出登录</el-button>
      </el-header>
      <el-container>
        <!-- 左侧导航 -->
        <el-aside width="200px">
           <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      background-color="blue"
      text-color="#fff"
      active-text-color="#ffd04b"
      router
    >
      <!-- 用户管理 -->
      <el-submenu index="user">
        <template slot="title">
          <i class="el-icon-user-solid"></i>
          <span>用户</span>
        </template>
        <el-menu-item index="about">用户列表</el-menu-item>
      </el-submenu>
      <!-- 教师管理 -->
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-s-marketing"></i>
          <span>教师</span>
        </template>
        <el-menu-item index="zhujiao">助教管理</el-menu-item>

      </el-submenu>

      <!-- 统计 -->
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-s-order"></i>
          <span>统计</span>
        </template>
        <el-menu-item index="student">教师</el-menu-item>
        <el-menu-item index="zhujiao">助教</el-menu-item>
      </el-submenu>
    </el-menu>

        </el-aside>
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{

    }
  },
  methods:{
    // 退出登录移除token
    dict(){
       localStorage.removeItem("TOKEN");
      window.location.reload();
    }
  }
};
</script>

<style scoped>
.el-header{
    background-color: #196bd6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    /* line-height: 160px; */
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
.el-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #fff;

}
</style>