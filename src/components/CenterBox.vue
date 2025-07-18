<script setup lang="ts">
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

const tableData = [
  {
    workshopName: "车间1",
    details: [
      { id: "101", description: "明细1描述", quantity: 10, status: "已完成" },
      { id: "102", description: "明细2描述", quantity: 20, status: "进行中" },
    ],
    subDetails: [
      { process: "工序1", name: "张三", capacity: 100 },
      { process: "工序2", name: "李四", capacity: 150 },
    ],
  },
  {
    workshopName: "车间2",
    details: [
      { id: "201", description: "明细3描述", quantity: 30, status: "未开始" },
      { id: "202", description: "明细4描述", quantity: 40, status: "已完成" },
    ],
    subDetails: [
      { process: "工序3", name: "王五", capacity: 200 },
      { process: "工序4", name: "赵六", capacity: 250 },
    ],
  },
  {
    workshopName: "车间3",
    details: [
      { id: "301", description: "明细5描述", quantity: 50, status: "进行中" },
      { id: "302", description: "明细6描述", quantity: 60, status: "未开始" },
    ],
    subDetails: [
      { process: "工序5", name: "孙七", capacity: 300 },
      { process: "工序6", name: "周八", capacity: 350 },
    ],
  },
];
</script>

<template>
  <div class="centerBox">
    <div class="setButton" style="padding: 10px">
      <div class="leftBut">
        <el-button type="success" plain>编辑</el-button>
        <el-button type="primary" plain>新增</el-button>
        <el-button type="danger" plain>删除</el-button>
        <el-button type="warning" plain>导入</el-button>
        <el-button type="warning" plain>导出</el-button>
      </div>
      <div class="rightBut">
        <el-button type="info" plain>按钮一</el-button>
        <el-button type="info" plain>按钮二</el-button>
      </div>
    </div>
    <div class="selfBox" style="padding: 10px">
      <el-descriptions :column="3" border>
        <el-descriptions-item
          label="Username"
          label-align="right"
          align="center"
          label-class-name="my-label"
          class-name="my-content"
          width="150px"
        >
          kooriookami
        </el-descriptions-item>
        <el-descriptions-item
          label="Telephone"
          label-align="right"
          align="center"
        >
          18100000000
        </el-descriptions-item>
        <el-descriptions-item label="Place" label-align="right" align="center">
          Suzhou
        </el-descriptions-item>
        <el-descriptions-item
          label="Remarks"
          label-align="right"
          align="center"
        >
          <el-tag size="small">School</el-tag>
        </el-descriptions-item>
        <el-descriptions-item
          label="Address"
          label-align="right"
          align="center"
        >
          No.1188, Wuzhong Avenue, Wuzhong District, Suzhou, Jiangsu Province
        </el-descriptions-item>
      </el-descriptions>
    </div>
    <div class="tableBox1" style="padding: 10px">
      <el-table :data="tableData[+active].details" style="width: 100%" border>
        <el-table-column prop="id" label="编号" min-width="80" />
        <el-table-column prop="description" label="描述" min-width="100" />
        <el-table-column prop="quantity" label="数量" min-width="80" />
        <el-table-column prop="status" label="状态" min-width="100" />
      </el-table>
    </div>
    <div class="tableBox2" style="padding: 10px">
      <el-table
        :data="tableData[+active].subDetails"
        style="width: 100%"
        border
      >
        <el-table-column prop="process" label="工序" min-width="80" />
        <el-table-column prop="name" label="姓名" min-width="80" />
        <el-table-column prop="capacity" label="产能" min-width="80" />
      </el-table>
    </div>
    <div class="switchButton" style="padding: 10px">
      <el-button
        v-for="(item, index) in tableData"
        :key="index"
        :type="active == index.toString() ? 'primary' : ''"
        @click="active = index.toString()"
      >
        {{ item.workshopName }}
      </el-button>
    </div>
  </div>
</template>

<style lang="scss">
.centerBox {
  flex: 1;
  margin: 15px;
  overflow: auto;
  display: flex;
  flex-direction: column;
}
.tableBox1,
.tableBox2 {
  flex: 1;
  height: 0;
}
.setButton {
  display: flex;
}
.leftBut {
  border-right: 1px solid #ccc;
  margin-right: 10px;
  padding-right: 10px;
}
</style>
