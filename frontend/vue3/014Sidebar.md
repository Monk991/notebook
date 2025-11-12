## Sidebar

- /src/components/AppLayout/Sidebar/index.vue

```vue
<template>
  <div class="sidebar">
    <Logo />
    <div class="menu-box">
      <el-menu
        :default-active="activeMenu"
        :collapse="appStore.collapsed"
        background-color="#304156"
        text-color="#bfcbd9"
        active-text-color="#409eff"
        :unique-opened="false"
        mode="vertical"
      >
        <sub-menu
          v-for="menu in menuList"
          :item="menu"
          :key="menu.name"
          :base-path="menu.path"
        ></sub-menu>
      </el-menu>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { useAppStore } from '@/store/app'

const appStore = useAppStore()

const route = useRoute()

// 当前激活菜单
const activeMenu = computed(() => {
  const { meta, name } = route
  if (meta.activeMenu) {
    return meta.activeMenu as string
  }
  return name
})

let menuList = [
  {
    path: '/sys',
    name: 'sys',
    redirect: '/sys/user',
    meta: {
      title: '系统管理'
    },
    children: [
      {
        path: 'user',
        name: 'sys-user',
        meta: {
          title: '管理员列表'
        }
      },
      {
        path: 'role',
        name: 'sys-role',
        meta: {
          title: '角色列表'
        }
      },
      {
        path: 'menu',
        name: 'sys-menu',
        meta: {
          title: '菜单管理'
        }
      }
    ]
  }
]
</script>
<style lang="scss" scoped>
.menu-box {
  overflow: auto;

  height: calc(100% - 50px);

  background-color: #304156;

  // 隐藏滚动条
  &::-webkit-scrollbar {
    width: 0;
  }
}

.el-menu {
  border-right: 0;
}
</style>
```

- /src/components/AppLayout/Sidebar/SubMenu.vue

```vue
<template>
  <template v-if="item.meta && !item.meta.hidden">
    <el-sub-menu v-if="hasShowingChild" :index="item.name">
      <template #title>
        <el-icon>
          <Icon icon="akar-icons:search" />
        </el-icon>
        <span>{{ item.meta.title }}</span>
      </template>
      <sub-menu
        v-for="child in item.children"
        :key="child.name"
        :item="child"
        :base-path="resolvePath(child.path)"
      />
    </el-sub-menu>

    <el-menu-item v-else :index="item.name" @click="navRoute()">
      <el-icon>
        <location />
      </el-icon>
      <template #title>
        {{ item.meta.title }}
      </template>
    </el-menu-item>
  </template>
</template>
<script setup lang="ts">
import { Icon } from '@iconify/vue'

const props = defineProps({
  item: {
    type: Object,
    required: true
  },
  basePath: {
    type: String,
    required: true
  }
})

// 判断是否有子菜单
const hasShowingChild = computed(() => {
  let children = props.item.children
  if (!children) {
    return false
  }
  const showingChildren = children.filter((child: any) => {
    return !(child.meta && child.meta.hidden)
  })

  if (showingChildren.length > 0) {
    return true
  }
  return false
})

// 菜单跳转
let router = useRouter()

let navRoute = () => {
  router.push({ path: props.basePath })
}

const resolvePath = (path: string) => {
  return props.basePath + '/' + path
}
</script>
```

- /src/router/index.ts

```ts
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'

const routes: Array<RouteRecordRaw> = [
  {
    path: '/sys',
    redirect: '/sys/user',
    children: [
      {
        path: 'user',
        name: 'sys-user',
        component: () => import('@/views/sys/user/index.vue'),
        meta: {
          title: '管理员列表'
        }
      },
      {
        path: 'role',
        name: 'sys-role',
        component: () => import('@/views/sys/role/index.vue'),
        meta: {
          title: '角色列表'
        }
      },
      {
        path: 'menu',
        name: 'sys-menu',
        component: () => import('@/views/sys/menu/index.vue'),
        meta: {
          title: '菜单管理'
        }
      }
    ]
  }
]

const router = createRouter({
  history: createWebHistory(),
  routes: routes
})

export default router
```

- /src/components/AppLayout/MainLayout.vue

```vue
<template>
  <div class="main-layout">
    <Navbar class="navbar" />
    <div class="main-container">
      <RouterView />
    </div>
  </div>
</template>
<style lang="scss" scoped>
// ...
</style>
```
