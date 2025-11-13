### Nuxt-Logo

* components/layout/header/Logo.vue

```vue
<template>
  <NuxtLink to="/" class="flex">
    <NuxtImg src="/logo.svg" class="h-7 dark:hidden" />
    <NuxtImg src="/logo-dark.svg" class="hidden h-7 dark:block" />
    <span class="ml-3 self-center font-bold">
      Title
    </span>
  </NuxtLink>
</template>
```

* components/layout/header/index.vue

```vue
<template>
  <header class="sticky top-0 z-40 bg-background/80 backdrop-blur-lg lg:border-b">
    <div
      class="flex h-14 items-center justify-between gap-2 px-4 md:px-8 border-b lg:border-none container max-w-screen-2xl">
      <LayoutHeaderLogo class="hidden flex-1 md:flex" />
    </div>
  </header>
</template>
```