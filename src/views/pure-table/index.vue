<script setup lang="ts">
import { list } from "./base/list";

defineOptions({
  name: "PureTable"
});
</script>

<template>
  <el-card>
    <template #header>
      <div class="card-header">
        <span class="font-medium">
          平台二次封装 element-plus 的 Table ，完全兼容 Api
          并提供灵活的配置项以及完善的类型提醒，再也不用将代码都写在 template
          里了，欢迎 Star
          <el-link
            href="https://github.com/xiaoxian521/pure-admin-table"
            target="_blank"
            style="font-size: 16px; margin: 0 4px 5px"
          >
            @pureadmin/table
          </el-link>
        </span>
      </div>
    </template>

    <el-alert
      title="基础用法中大部分表格都没设置 row-key ，不过最好都设置一下，后端需返回唯一值的字段，比如id 作用：1. 用来优化 Table
      的渲染，尤其当字段在深层结构中；2. 防止某些操作导致表格组件内部混乱"
      type="info"
      :closable="false"
    />

    <el-tabs>
      <template v-for="(item, index) of list" :key="item.key">
        <el-tab-pane>
          <template #label>
            <el-tooltip
              :content="`（第 ${index + 1} 个示例）${item.content}`"
              placement="top-end"
            >
              <span>{{ item.title }}</span>
            </el-tooltip>
          </template>
          <component :is="item.component" />
        </el-tab-pane>
      </template>
    </el-tabs>
  </el-card>
</template>

<style scoped>
:deep(.el-tabs__nav-wrap)::after {
  height: 1px;
}

:deep(.el-tabs__header) {
  margin-top: 10px;
}

:deep(.el-alert__title) {
  font-size: 16px;
}
</style>
