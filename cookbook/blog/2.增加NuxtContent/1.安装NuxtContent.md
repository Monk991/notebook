## [安装 NuxtContent](https://content.nuxt.com/docs/getting-started/installation)

```bash
E:\ws-blog\monk-blog>yarn add @nuxt/content
yarn add v1.22.22
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
warning " > @tailwindcss/vite@4.1.17" has unmet peer dependency "vite@^5.2.0 || ^6 || ^7".
warning "nuxt > @nuxt/devtools@3.1.0" has unmet peer dependency "vite@>=6.0".
warning "nuxt > unplugin-vue-router@0.16.1" has unmet peer dependency "@vue/compiler-sfc@^3.5.17".
warning "nuxt > @nuxt/devtools > @nuxt/devtools-kit@3.1.0" has unmet peer dependency "vite@>=6.0".
warning "nuxt > @nuxt/devtools > vite-plugin-inspect@11.3.3" has unmet peer dependency "vite@^6.0.0 || ^7.0.0-0".
warning "nuxt > @nuxt/devtools > vite-plugin-vue-tracer@1.1.3" has unmet peer dependency "vite@^6.0.0 || ^7.0.0".
warning "nuxt > @nuxt/devtools > @vue/devtools-core > vite-hot-client@2.1.0" has unmet peer dependency "vite@^2.6.0 || ^3.0.0 || ^4.0.0 || ^5.0.0-0 || ^6.0.0-0 || ^7.0.0-0".
warning "nuxt > @nuxt/devtools > vite-plugin-inspect > vite-dev-rpc@1.1.0" has unmet peer dependency "vite@^2.9.0 || ^3.0.0-0 || ^4.0.0-0 || ^5.0.0-0 || ^6.0.1 || ^7.0.0-0".
[4/4] Building fresh packages...

success Saved lockfile.
success Saved 120 new dependencies.
info Direct dependencies
└─ @nuxt/content@3.8.0
info All dependencies
├─ @apidevtools/json-schema-ref-parser@11.9.3
├─ @isaacs/balanced-match@4.0.1
// ...
├─ xmlhttprequest-ssl@2.1.2
├─ zod-to-json-schema@3.24.6
└─ zod@3.25.76
$ nuxt prepare
√ Types generated in .nuxt                                                                               nuxi 21:13:56
Done in 24.87s.
```

- nuxt.config.ts

```ts
import tailwindcss from "@tailwindcss/vite";

export default defineNuxtConfig({
  // ....
  // 增加'@nuxt/content'
  modules: ["shadcn-nuxt", "@nuxt/content"],
  // ....
});
```

- 增加 content.config.ts

```ts
import { defineContentConfig, defineCollection } from "@nuxt/content";

export default defineContentConfig({
  collections: {
    content: defineCollection({
      type: "page",
      source: "**/*.md",
    }),
  },
});
```

- content/index.md

```md
# My First Page

Here is some content.
```

- app/pages/index.vue

```vue
<script setup lang="ts">
const { data: home } = await useAsyncData(() =>
  queryCollection("content").path("/").first()
);

useSeoMeta({
  title: home.value?.title,
  description: home.value?.description,
});
</script>

<template>
  <ContentRenderer v-if="home" :value="home" />
  <div v-else>Home not found</div>
</template>
```

- app.vue

```vue
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
```
