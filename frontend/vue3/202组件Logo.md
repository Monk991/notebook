## Logo

### 组件

- /src/components/AppLayout/Sidebar/Log.vue

```vue
<template>
  <div class="logo-box">
    <router-link
      v-if="appStore.collapsed"
      key="collapse"
      class="logo-link"
      to="/"
    >
      <img src="../../../assets/vue.svg" class="logo" />
    </router-link>

    <router-link v-else key="expand" class="logo-link" to="/">
      <img src="../../../assets/vue.svg" class="logo" />
      <span class="title">后台管理</span>
    </router-link>
  </div>
</template>

<script setup lang="ts">
import { useAppStore } from '@/store/app'

const appStore = useAppStore()
</script>

<style lang="scss" scoped>
.logo-box {
  position: relative;

  display: flex;

  overflow: hidden;

  align-items: center;

  width: 100%;

  height: 50px;

  background: #2b2f3a;

  box-shadow: 0 1px 4px rgba(0, 21, 41, 0.08);

  text-align: center;

  line-height: 50px;

  .logo-link {
    width: 100%;

    height: 100%;

    .logo {
      width: 20px;

      height: 20px;

      vertical-align: middle;
    }

    .title {
      display: inline-block;

      margin-left: 12px;

      color: #fff;

      vertical-align: middle;

      font-weight: 600;

      font-size: 16px;

      line-height: 50px;
    }
  }
}
</style>
```
