## Navbar

- /src/components/AppLayout/Navbar.vue

```vue
<template>
  <div class="navbar">
    <hamburger
      class="hanburger-box"
      :is-active="!appStore.collapsed"
      @toggleClick="toggleSideBar"
    />
  </div>
</template>
<script lang="ts" setup>
import { useAppStore } from '@/store/app'

const appStore = useAppStore()

function toggleSideBar() {
  appStore.collapsed = !appStore.collapsed
}
</script>
<style lang="scss" scoped>
.navbar {
  display: flex;

  align-items: center;

  flex-direction: row;

  justify-content: space-between;

  box-sizing: border-box;

  height: 50px;

  background: #fff;

  box-shadow: 0 1px 4px rgba(0, 21, 41, 0.08);

  .hanburger-box {
    cursor: pointer;
  }
}
</style>
```

- /src/store/app.ts

```ts
import { defineStore } from 'pinia'

export const useAppStore = defineStore('app', {
  state: () => {
    return {
      collapsed: false
    }
  },
  persist: [
    {
      storage: localStorage
    }
  ]
})
```

- /src/components/MainLayout.vue

```vue
<template>
  <div class="app-layout" :class="{ collapsed: appStore.collapsed }">
    <Sidebar class="sidebar" />

    <MainLayout class="main-layout" />
  </div>
</template>
<script setup lang="ts">
import { useAppStore } from '@/store/app'

const appStore = useAppStore()
</script>
```
