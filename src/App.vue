<template>
  <div>
    <el-container class="desktop-layout">
      <el-aside :width="asideWidth" id="aside">
        <Aside @change="changeAside"></Aside>
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
  import { ref } from 'vue';
  import Aside from './components/Aside.vue';
  import Footer from './components/Footer.vue';

  const asideWidth = ref('200px')

  // Emit Event
  function changeAside(close: boolean) {
    const width = close ? '64px' : '200px'
    if (close) {
      setTimeout(() => asideWidth.value = width, 275)
    } else {
      asideWidth.value = width
    }
  }
</script>

<style scoped lang="less">
  .desktop-layout {
    height: 100vh;

    #footer {
      height: 22px;
    }
  }
</style>