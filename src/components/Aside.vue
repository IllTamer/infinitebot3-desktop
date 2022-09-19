<template>
  <div class="aside">
    <!-- 侧边栏 -->
    <div class="menu">
      <el-menu
        default-active="2"
        class="aside-el-menu-vertical"
        :collapse="isCollapse"
      >
        <el-menu-item index="1" @click="isCollapse = !isCollapse">
          <el-icon v-if="isCollapse"><ArrowRight/></el-icon>
          <el-icon v-else><ArrowDown/></el-icon>
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
    <div class="background"></div>
    <Transition name="status">
      <div v-if="!isCollapse" class="status"></div>
      <div v-else="isCollapse" class="status" style="width: 64px"></div>
    </Transition>
  </div>
</template>

<script setup lang="ts">
  import { ref, watch } from 'vue'
  import {
    ArrowDown,
    ArrowRight,
    Menu as IconMenu,
    Document,
    Setting,
  } from '@element-plus/icons-vue'

  const isCollapse = ref(false);

  watch(isCollapse, () => {
    recall(isCollapse.value);
  });

  const emits = defineEmits(['change']);
  const recall = (change: boolean): void => {
    emits('change', change);
  }
</script>

<style scoped lang="less">
  .aside {
    // background-color: #e9ebee;
    width: 100%;
    height: 100%;
  }

  .aside-el-menu-vertical {
    min-height: 100%;
  }

  .menu {
    height: 100%;
  }
  .background {
    width: 200px;
    height: 22px;
    position: fixed;
    bottom: 0;
    z-index: 999;
    background-color: #e9ebee;
  }
  .status {
    .background;
    background-color: #54d1b0;

    // el-menu 动画
    // cubic-bezier(0.645, 0.045, 0.355, 1)
    // cubic-bezier(0.23, 1, 0.32, 1)
    &-enter-active,
    &-leave-active {
      transition: all 0.3s cubic-bezier(0.52, 0.09, 0.30, 1);
    }

    &-enter-from,
    &-leave-to {
      width: 64px;
    }
  }
</style>