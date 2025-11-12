## 基础布局

- /src/components/AppLayout/indev.vue

```vue
<template>
  <div class="app-layout collapsed">
    <Sidebar class="sidebar" />

    <MainLayout class="main-layout" />
  </div>
</template>
<script setup lang="ts">
import { useAppStore } from '@/store/app'

const appStore = useAppStore()
</script>

<style lang="scss">
$expendedWidth: 210px;
$collapseWidth: 64px;

.app-layout {
  box-sizing: border-box;

  height: 100vh;

  .sidebar {
    position: fixed;

    top: 0;

    bottom: 0;

    left: 0;

    overflow: hidden;

    width: $expendedWidth;

    height: 100%;

    transition: width 0.28s;
  }

  .main-layout {
    margin-left: $expendedWidth;

    transition: margin-left 0.28s;

    .navbar {
      width: calc(100% - $expendedWidth);
    }
  }

  &.collapsed {
    .sidebar {
      width: $collapseWidth;
    }

    .main-layout {
      margin-left: $collapseWidth;

      .navbar {
        width: calc(100% - $collapseWidth);
      }
    }
  }
}
</style>
```

- /src/components/AppLayout/Sidebar/index.vue

```vue
<template>
  <div class="sidebar">Sidebar</div>
</template>
<style lang="scss" scoped></style>
```

- /src/components/AppLayout/MainLayout.vue

```vue
<template>
  <div class="main-layout">
    <Navbar class="navbar" />
    <div class="main-container">Main</div>
  </div>
</template>
<style lang="scss" scoped>
.main-layout {
  position: relative;

  height: 100%;

  .navbar {
    position: fixed;

    top: 0;

    right: 0;

    z-index: 9;

    transition: width 0.28s;
  }

  .main-container {
    position: absolute;

    top: 50px;

    overflow: auto;

    width: 100%;

    height: calc(100% - 50px);
  }
}
</style>
```

- /src/components/AppLayout/Navbar.vue

```vue
<template>
  <div class="navbar">Navbar</div>
</template>
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
