## Nuxt使用AppConfig

* app.config.ts

```ts
export default defineAppConfig({
  header: {
    title: 'Nuxt模版',
    showTitle: true,
    logo : {
      light: '/logo.svg',
      dark: '/logo-dark.svg',
    }
  }
})
```

* components/layout/header/Logo.vue

```vue
<template>
  <div>
    <NuxtLink v-if="logo.light && logo.dark" to="/" class="flex">
      <NuxtImg :src="logo.light" class="h-7 dark:hidden" />
      <NuxtImg :src="logo.dark" class="hidden h-7 dark:block" />
      <span v-if="showTitle && title" class="ml-3 self-center font-bold">
        {{ title }}
      </span>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
const { logo, title, showTitle } = useAppConfig().header
</script>
```