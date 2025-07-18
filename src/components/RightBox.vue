<script setup lang="ts">
import { ref } from "vue";
import { CaretLeft } from "@element-plus/icons-vue";

const drawer = ref(false);
</script>

<template>
  <div class="rightBox">
    <div class="arrow" @click="drawer = true">
      <el-icon size="25"><CaretLeft /></el-icon>
    </div>
    <el-drawer v-model="drawer" title="I am the title" :with-header="false">
      <span>Hi there!</span>
    </el-drawer>
  </div>
</template>

<style lang="scss">
.rightBox {
  width: 0;
  padding-left: 15px;
  flex-shrink: 0;
  position: relative;
  .arrow {
    position: absolute;
    top: 50%;
    transform: translate(0, 50%);
    right: 0;
    cursor: pointer;
  }
}
</style>
