<script setup lang="ts">
import LeftBox from "./components/LeftBox.vue";
import CenterBox from "./components/CenterBox.vue";
import RightBox from "./components/RightBox.vue";
import { ref } from "vue";

const activeRouter = ref("0");
</script>

<template>
  <div class="container">
    <LeftBox v-model="activeRouter" />
    <CenterBox v-model="activeRouter" />
    <RightBox />
  </div>
</template>

<style lang="scss">
.container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: row;
}
</style>
