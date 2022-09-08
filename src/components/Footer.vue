<template>
  <div class="footer">
    <div class="others">
      <!-- 版本 -->
      <span>v{{packageJson.version}}</span>
      <!-- 设置项 -->
      <el-dropdown>
        <el-icon class="setting" :size="16">
          <Setting />
        </el-icon>
        <template #dropdown>
          <el-dropdown-menu>
            <el-dropdown-item>View</el-dropdown-item>
            <el-dropdown-item>Add</el-dropdown-item>
            <el-dropdown-item>Delete</el-dropdown-item>
          </el-dropdown-menu>
        </template>
      </el-dropdown>
    </div>
  </div>
</template>

<script setup lang="ts">
  import packageJson from '../../package.json';

</script>

<style scoped lang="less">
  .others {
    span {
      display: inline-block;
    }
    .setting {
      margin-left: 16px;
      margin-right: 16px;
    } 
  }
  .footer {
    background-color: #e9ebee;
    width: 100%;
    height: 100%;
    font-size: 12px;
    // 竖直居中
    display: flex;
    align-items: center;
    // 水平靠右
    justify-content: right;
    text-align: right;
  }
</style>