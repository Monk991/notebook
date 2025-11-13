## Header

* components/layout/header/index.vue

```vue
<template>
  <header class="sticky top-0 z-40 bg-background/80 backdrop-blur-lg lg:border-b">
    <div
      class="flex h-14 items-center justify-between gap-2 px-4 md:px-8 border-b lg:border-none container max-w-screen-2xl">
      Title
    </div>
  </header>
</template>
```

* app.vue

```vue
<template>
  <LayoutHeader />
</template>
```