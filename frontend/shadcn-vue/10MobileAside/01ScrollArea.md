## [ScrollArea](https://www.shadcn-vue.com/docs/components/scroll-area.html)

### 安装

```bash
PS E:\phoenix\blog\workspace\blog-portal> npx shadcn-vue@latest add scroll-area
✔ Checking registry.
yarn add v1.22.22

... 

Done in 6.04s.
```

### 使用

* components/layout/aside/index.vue

```vue
<template>
    <UiScrollArea orientaion="vertical" class="relative h-full overflow-hidden py-6 pr-6 text-sm md:pr-4" type="hover">
        <div style="height: 300px;" class=" bg-red-300 "> </div>
        <div style="height:300px;" class="bg-green-300 "> </div>
        <div style="height: 300px;" class="bg-yellow-300 "> </div>
    </UiScrollArea>
</template>
<script setup lang="ts">
defineProps<{ isMobile: boolean }>();
</script>
```