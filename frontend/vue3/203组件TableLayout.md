## 带分页的表格组件

### 组件

- /src/components/TableLayout.vue

```vue
<template>
  <el-card class="table-layout">
    <template #header>
      <slot name="header" />
    </template>
    <main>
      <el-table
        :data="dataList"
        style="width: 100%"
        v-loading="loading"
        @selection-change="handleSelectionChange"
      >
        <slot name="main" />

        <template #append>
          <el-pagination
            background
            layout="prev, pager, next"
            :total="total"
            class="table-footer"
            :current-page="currentPage"
            :page-size="pageSize"
            :pager-count="5"
            @current-change="handleQuery"
          />
        </template>
      </el-table>
    </main>
  </el-card>
</template>
<script setup lang="ts">
type Props = {
  total: number
  dataList: Array<any>
  pageSize?: number
  loading?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  total: 0,
  dataList: () => [],
  pageSize: 15,
  loading: false
})

const currentPage = ref(1)

const emit = defineEmits(['query', 'selection'])

function handleQuery(curPage: number) {
  currentPage.value = curPage
  emit('query', curPage, props.pageSize)
}

function handleSelectionChange(selections: any) {
  let selectionIds = selections.map((item: any) => item.id)
  emit('selection', selectionIds)
}
</script>
<style lang="scss" scoped>
.table-footer {
  height: 60px;
  float: right;
}
</style>
```

### 使用

- /src/views/blog/article/index.vue

```vue
<template>
  <div class="article">
    <TableLayout
      :loading="loading"
      :total="total"
      :dataList="dataList"
      @query="handleQuery"
      @selection="handleSelection"
    >
      <template #header>
        <el-button type="primary" @click="handleAdd">新增</el-button>
        <el-button
          type="danger"
          :disabled="ids.length === 0"
          @click="handleDelete"
          >删除</el-button
        >
      </template>
      <template #main>
        <el-table-column type="selection" width="50" align="center" />
        <el-table-column prop="date" label="Date" width="180" />
        <el-table-column prop="name" label="Name" width="180" />
        <el-table-column prop="address" label="Address" />
        <el-table-column label="操作" align="center" width="120">
          <template #default="scope">
            <el-button type="primary" link @click="handleUpdate(scope.row.id)">
              编辑
            </el-button>
            <el-button type="danger" link @click="handleDelete(scope.row.id)">
              删除
            </el-button>
          </template>
        </el-table-column>
      </template>
    </TableLayout>
  </div>
</template>
<script setup lang="ts">
const state = reactive<{
  loading: Boolean
  total: number
  dataList: Array<any>
}>({
  loading: false,
  total: 0,
  dataList: []
})

const { total, dataList, loading } = toRefs(state)

onMounted(() => {
  handleQuery(1)
})

const handleQuery = async (curPage: number, pageSize: number = 15) => {
  if (state.loading) {
    return
  }
  state.loading = true
  try {
    state.total = 100
    state.dataList = [
      {
        id: '1',
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }
    ]
  } finally {
    state.loading = false
  }
}

const editRef = ref()

// 新增
const handleAdd = () => {
  editRef.value.show()
}

// 更新
const handleUpdate = async (id: any) => {
  editRef.value.show(id)
}

// 删除
let ids: Ref<Array<string>> = ref([])

const handleSelection = (selectionIds: Array<string>) => {
  ids.value = selectionIds
}

const handleDelete = async (id: string) => {
  const deleteIds = id || ids.value.join(',')
  ElMessageBox.confirm('是否确认删除选中的数据项?', '警告', {
    confirmButtonText: '确定',
    cancelButtonText: '取消',
    type: 'warning'
  }).then(() => {
    // TODO 删除操作
    ElMessage.success('删除成功')
    handleQuery(1)
  })
}
</script>
```
