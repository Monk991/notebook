## 面包屑

### 组件

- /src/components/Breadcrumb.vue

```vue
<template>
  <el-breadcrumb class="app-breadcrumb" separator-class="el-icon-arrow-right">
    <transition-group name="breadcrumb">
      <el-breadcrumb-item v-for="(item, index) in breadcrumbs" :key="item.path">
        <span v-if="item.redirect === 'noredirect' || index === breadcrumbs.length - 1" class="no-redirect">{{
          item.meta.title
        }}</span>
        <a v-else @click.prevent="handleLink(item)">
          {{ item.meta.title }}
        </a>
      </el-breadcrumb-item>
    </transition-group>
  </el-breadcrumb>
</template>

<script setup lang="ts">
import { RouteLocationMatched } from 'vue-router'

const currentRoute = useRoute()

const breadcrumbs = ref([] as Array<RouteLocationMatched>)

function getBreadcrumb() {
  let matched = currentRoute.matched.filter((item) => item.meta && item.meta.title)

  const first = matched[0]
  if (!first) {
    matched = [{ path: '/', meta: { title: '概览' } } as any]
  }
  breadcrumbs.value = matched.filter((item) => {
    return item.meta && item.meta.title && item.meta.breadcrumb !== false
  })
}

let router = useRouter()

function handleLink(item: any) {
  const { path } = item
  router.push({ path })
}

watch(
  () => currentRoute.path,
  (path) => {
    if (path.startsWith('/redirect/')) {
      return
    }
    getBreadcrumb()
  }
)

onBeforeMount(() => {
  getBreadcrumb()
})
</script>

<style lang="scss" scoped>
.el-breadcrumb__inner,
.el-breadcrumb__inner a {
  font-weight: 400 !important;
}

.app-breadcrumb.el-breadcrumb {
  display: inline-block;
  font-size: 14px;
  line-height: 50px;
  margin-left: 8px;

  .no-redirect {
    color: #97a8be;
    cursor: text;
  }
}
</style>
```

- /src/components/AppLayout/Navbar.vue

```vue
<template>
  <div class="navbar">
    <hamburger class="hanburger-box" :is-active="!appStore.collapsed" @toggleClick="toggleSideBar" />
    <breadcrumb class="breadcrumb-container" />
    <el-dropdown trigger="click" class="right-menu">
      <!-- ... -->
    </el-dropdown>
  </div>
</template>
<script lang="ts" setup>
// ...
</script>
<style lang="scss" scoped>
.navbar {
  //  ...

  .breadcrumb-container {
    flex: 1;
    float: left;
  }
}
</style>
```
