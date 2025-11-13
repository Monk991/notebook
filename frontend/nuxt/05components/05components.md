## [components)](https://nuxt.zhcndoc.com/docs/guide/directory-structure/components)

* components/Sidebar/Left/index.vue

```vue
<template>
    <div>
        LetSidebar
    </div>
</template>
```
* app.vue

```vue
<template>
  <div :class="{ dark: darkMode }">
    <div class="bg-white text-gray-900 dark:bg-gray-800 dark:text-white">
      <div class="min-h-full">
        <div class="mx-auto grid grid-cols-12 lg:max-w-7xl">
          <!-- Left -->
          <div class="hidden md:block lg:gap-5 xl:col-span-2">
            <div class="h-screen">
              <SidebarLeft />
            </div>
          </div>
          <!-- Main -->
          <div class="col-span-12 md:col-span-8 xl:col-span-6">Main</div>
          <div class="hidden md:col-span-3 md:block xl:col-span-4">Right</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const darkMode = ref(false);

onMounted(() => {});
</script>

```