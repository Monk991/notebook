## [NuxtImage](https://image.nuxt.com/get-started/installation)

### 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx nuxi@latest module add @nuxt/image
Need to install the following packages:
nuxi@3.23.1
Ok to proceed? (y) y

...

✔ Types generated in .nuxt  
```

### 使用

* app.vue

```vue
<template>
  <NuxtImg  src="logo.svg" class="h-7 dark:hidden" />
</template>
```