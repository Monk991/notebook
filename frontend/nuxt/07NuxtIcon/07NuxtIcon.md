## [NuxtIcon](https://nuxt.com/modules/icon)

### 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx nuxi module add icon
```

### 使用NuxtIcon替换"@iconify/vue"

* components/DarkModeToggle.vue

```vue
<template>
  <UiButton variant="ghost" size="icon" @click="toggleDark">
    <Icon name="lucide:moon" class=" rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0" size="18" />
    <Icon name="lucide:sun" class="absolute rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
      size="18" />
    <span class="sr-only">Toggle theme</span>
  </UiButton>
</template>

<script setup lang="ts">
const colorMode = useColorMode();

function toggleDark() {
  colorMode.preference = colorMode.value === "dark" ? "light" : "dark";
}
</script>

```