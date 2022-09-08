<template>
  <div>
    <el-container class="desktop-layout">
      <el-aside id="aside">
          <Aside></Aside>
      </el-aside>
      <el-container>
        <el-main>Main</el-main>
        <el-footer id="footer" class="clear-padding">
          <Footer></Footer>
        </el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<script setup lang="ts">
  import Aside from './components/Aside.vue';
  import Footer from './components/Footer.vue';
</script>

<style scoped lang="less">
  .desktop-layout {
    height: 100vh;

    #aside {
      width: 200px;
    }
    #footer {
      height: 22px;
    }
  }
</style>