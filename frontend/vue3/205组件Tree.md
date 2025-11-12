## 树形结构

### 组件

- /src/views/blog/cate/index.vue

```vue
<template>
  <div class="cate">
    <el-card class="cate-box">
      <template #header>
        <div class="card-header">
          <span>分类</span>
          <el-button type="primary" text @click="handleShowCate('0')">添加分类</el-button>
        </div>
      </template>
      <el-tree
        node-key="id"
        :data="cateList"
        :props="defaultProps"
        :default-expand-all="true"
        :expand-on-click-node="false"
        @node-click="handleNodeClick"
      >
        <template #default="{ node, data }">
          <div class="tree-node">
            <span>{{ node.label }}</span>
            <span class="tree-btns">
              <el-button
                type="primary"
                v-if="node.level == 1"
                plain
                @click.stop="handleShowCate(data.id)"
                :icon="Plus"
                size="small"
              />
              <el-button type="primary" plain v-else @click.stop="handleEditCate(data)" :icon="Edit" size="small" />
              <el-button
                type="danger"
                v-if="node.childNodes.length == 0"
                plain
                @click.stop="handleRemoveCate(data)"
                :icon="Delete"
                size="small"
              />
            </span>
          </div>
        </template>
      </el-tree>
    </el-card>
    <el-card class="tag-box">
      <template #header>
        <div class="card-header">
          <span>分类</span>
          <el-button type="primary" text>新增标签</el-button>
        </div>
      </template>

      <div v-for="item in tagList" :key="item.id">
        <el-tag class="ml-2" :color="item.color">{{ item.name }}</el-tag>
      </div>
    </el-card>

    <el-dialog
      v-model="cateDialogVisible"
      title="分类"
      width="300"
      @close="handleCateClose"
      :close-on-click-modal="false"
    >
      <el-form ref="cateFormRef" :model="cateForm" :rules="cateRules">
        <el-form-item>
          <el-input v-model="cateForm.name" placeholder="请输入名称" />
        </el-form-item>
      </el-form>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="cateDialogVisible = false">取消</el-button>
          <el-button type="primary" @click="handleSubmitCate"> 确定 </el-button>
        </span>
      </template>
    </el-dialog>
  </div>
</template>
<script setup lang="ts">
import { Ref, onMounted, ref } from 'vue'
import { Delete, Plus, Edit } from '@element-plus/icons-vue'
import { deleteCate, listCate, getCate, saveCate, updateCate } from '@/apis/blog/cate.ts'

interface Cate {
  id: string
  name: string
  pid: string
  children?: Cate[]
}

const cateList: Ref<Cate[]> = ref([])

onMounted(() => {
  initDate()
})

const initDate = async () => {
  let { data } = await listCate()
  cateList.value = data
}

const defaultProps = {
  children: 'children',
  label: 'name'
}

const tagList: Ref<any[]> = ref([])

const handleNodeClick = (node: any) => {
  console.info('node', node)
  tagList.value = [
    {
      id: '1',
      name: 'test',
      color: '#FF00FF'
    }
  ]
}

const cateDialogVisible = ref(false)

const cateFormRef: Ref<any> = ref()

const cateForm = ref({
  id: '',
  name: '',
  pid: ''
})

const cateRules = ref({
  name: [
    { required: true, message: '请输入分类名称', trigger: 'blur' },
    { min: 1, max: 32, message: '分类名称应在1到32个字符之间', trigger: 'blur' }
  ]
})

const handleShowCate = (pid: string) => {
  cateForm.value.pid = pid
  cateDialogVisible.value = true
}

const handleEditCate = async (cate: Cate) => {
  let { data } = await getCate(cate.id)
  cateForm.value = data
  cateDialogVisible.value = true
}

const handleSubmitCate = () => {
  if (!cateFormRef.value) return
  cateFormRef.value.validate(async (valid: boolean, fields: any) => {
    if (valid) {
      if (cateForm.value.id) {
        let { id, name, pid } = cateForm.value
        let { status } = await updateCate(cateForm.value.id, { id, name, pid })
        if (status == 200) {
          ElMessage.success('修改成功')
          cateDialogVisible.value = false
          initDate()
        }
      } else {
        let { status } = await saveCate(cateForm.value)
        if (status == 200) {
          ElMessage.success('保存成功')
          cateDialogVisible.value = false
          initDate()
        }
      }
    } else {
      console.log('error submit!', fields)
    }
  })
}

const handleRemoveCate = async (data: Cate) => {
  ElMessageBox.confirm(`是否删除[${data.name}]分类?`, '警告', {
    confirmButtonText: '确定',
    cancelButtonText: '取消',
    type: 'warning'
  })
    .then(async () => {
      let ids = [data.id]
      let { status } = await deleteCate(ids)
      if (status == 200) {
        ElMessage.success('删除成功')
        initDate()
      }
    })
    .catch(() => {})
}

const handleCateClose = () => {
  console.info('before close')
  cateForm.value.id = ''
  cateForm.value.name = ''
  cateForm.value.pid = '0'
}
</script>
<style lang="scss" scoped>
.cate {
  display: flex;
  flex-direction: row;
  .cate-box {
    min-width: 300px;
  }

  .tag-box {
    margin-left: 8px;
    flex: 1;
  }

  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
.tree-node {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 14px;
}

.tree-btns {
  display: flex;
  align-items: center;
}
</style>
<style lang="scss">
.el-tree-node__content {
  padding: 8px;
}
</style>
```
