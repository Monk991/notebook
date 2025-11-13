## [ShadcnSheet](https://www.shadcn-vue.com/docs/components/sheet.html)

### 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx shadcn-vue@latest add sheet

✔ Checking registry.

...

ℹ Updated 1 file:
  - lib/utils.ts   
```

### 使用

* components/layout/header/NavSheet.vue

```vue
<template>
  <UiSheet v-model:open="open">
    <UiSheetTrigger as-child>
      <UiButton variant="ghost" size="icon" class="md:hidden">
        <Icon name="lucide:menu" size="18" />
      </UiButton>
    </UiSheetTrigger>

    <UiSheetContent side="left" class="pr-0">
      <LayoutHeaderLogo />
      <LayoutAside/>
    </UiSheetContent>
  </UiSheet>
</template>

<script setup lang="ts">
import { LayoutAside } from '#components';

const open = ref(false)

watch(() => useRoute().path, () => {
  open.value = false
})

</script>
```

* components/layout/aside/index.vue

```vue
<template>
  Aside
</template>
```

* components/layout/header/index.vue

```vue
<template>
  <header class="sticky top-0 z-40 bg-background/80 backdrop-blur-lg lg:border-b">
    <div
      class="flex h-14 items-center justify-between gap-2 px-4 md:px-8 border-b lg:border-none container max-w-screen-2xl">
      <LayoutHeaderLogo class="hidden flex-1 md:flex" />
      <LayoutHeaderNavSheet />
      <LayoutHeaderLogo v-if="config.header.showTitleInMobile" class="flex md:hidden" />
      
      <div class="flex flex-1 justify-end gap-2">
        <DarkModeToggle />
      </div>
    </div>
  </header>
</template>
<script setup>
const config = useAppConfig()
</script>
```