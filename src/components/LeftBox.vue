<script setup lang="ts">
import {
  Document,
  Menu as IconMenu,
  Location,
  Setting,
  CaretRight,
} from "@element-plus/icons-vue";
import { computed, ref } from "vue";

interface Props {
  modelValue: string; // 当前页
}
interface Emit {
  (e: "update:modelValue", value: string): void;
}

const props = withDefaults(defineProps<Props>(), {});
const emit = defineEmits<Emit>();

const active = computed({
  get: () => props.modelValue,
  set: (val: string) => {
    emit("update:modelValue", val);
  },
});

const isHideMenu = ref(false); //隐藏左菜单
</script>

<template>
  <div :class="{ leftBox: true, hide: isHideMenu }">
    <el-menu
      class="el-menu-vertical-demo"
      :default-active="active"
      :class="{ hide: isHideMenu }"
    >
      <el-menu-item index="0" @click="active = '0'">
        <el-icon><icon-menu /></el-icon>
        一车间
      </el-menu-item>
      <el-menu-item index="1" @click="active = '1'">
        <el-icon><document /></el-icon>
        二车间
      </el-menu-item>
      <el-menu-item index="2" @click="active = '2'">
        <el-icon><setting /></el-icon>
        三车间
      </el-menu-item>
    </el-menu>

    <div class="arrow" @click="isHideMenu = !isHideMenu">
      <el-icon size="25"><CaretRight /></el-icon>
    </div>
  </div>
</template>

<style lang="scss">
.leftBox {
  width: 200px;
  height: 100%;
  padding: 10px;
  position: relative;
  overflow: hidden;
  transition: width 0.6s;
  flex-shrink: 0;
  &.hide {
    width: 0;
  }
}
.el-menu {
  height: 100%;
  overflow: hidden;
  transition: width 0.6s;
  background-color: #fcfcfc;
  &.hide {
    width: 0;
  }
}

.arrow {
  position: absolute;
  right: -5px;
  top: 50%;
  transform: translate(0, 50%);
  cursor: pointer;
  z-index: 10;
  color: #6d6c6c;
}
</style>
