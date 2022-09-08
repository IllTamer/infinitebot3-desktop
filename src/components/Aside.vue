<template>
  <div class="aside">
    <!-- 侧边栏 -->
    <div class="menu">
      <el-menu
        default-active="2"
        class="aside-el-menu-vertical"
        :collapse="isCollapse"
        @open="handleOpen"
        @close="handleClose"
      >
        <el-menu-item index="1" @click="isCollapse = !isCollapse">
          <!-- 不起作用 -->
          <Transition name="slide-up">
            <el-icon v-if="isCollapse"><ArrowRight/></el-icon>
            <el-icon v-else><ArrowDown/></el-icon>
          </Transition>
        </el-menu-item>
        <el-menu-item index="2">
          <el-icon><icon-menu /></el-icon>
          <template #title>Navigator Two</template>
        </el-menu-item>
        <el-menu-item index="3" disabled>
          <el-icon><document /></el-icon>
          <template #title>Navigator Three</template>
        </el-menu-item>
        <el-menu-item index="4">
          <el-icon><setting /></el-icon>
          <template #title>Navigator Four</template>
        </el-menu-item>
      </el-menu>
    </div>
    <!-- 状态栏 -->
    <div class="status"></div>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue'
  import {
    ArrowDown,
    ArrowRight,
    Menu as IconMenu,
    Document,
    Setting,
  } from '@element-plus/icons-vue'
  
  const isCollapse = ref(false)
  const handleOpen = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
  }
  const handleClose = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
  }

  function changeCollapse() {

  }
</script>

<style scoped lang="less">
  .aside {
    background-color: #e9ebee;
    width: 100%;
    height: 100%;
  }
  .aside-el-menu-vertical:not(.el-menu--collapse) {
    width: 200px;
    height: 100%;
  }
  .menu {
    // 动态计算
    height: calc(100% - 22px);
  }
  .status {
    height: 22px;
    width: auto;
    background-color: #54d1b0;
  }

  .slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.25s ease-out;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateY(30px);
}

.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>