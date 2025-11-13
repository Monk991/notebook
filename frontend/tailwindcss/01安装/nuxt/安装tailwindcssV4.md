## [Install Tailwind V4 CSS with Nuxt](https://tailwindcss.com/docs/installation/framework-guides/nuxt)

### 安装

* 网页路径

  Installation -> Framework Guides -> Nuxt

* 安装依赖

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add tailwindcss @tailwindcss/vite

yarn add v1.22.22
[1/4] 🔍  Resolving packages...
...
$ nuxt prepare
✔ Types generated in .nuxt                                                                                                      nuxi  10:28:10 AM
✨  Done in 12.49s.
```

* nuxt.config.ts

```ts
import tailwindcss from "@tailwindcss/vite";

// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-11-01',
  devtools: { enabled: true },
  vite: {
    plugins: [
      tailwindcss(),
    ],
  },
})
```

* assets/css/main.css

```css
@import "tailwindcss";
```

* nuxt.config.ts
* 
```
import tailwindcss from "@tailwindcss/vite";

// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-11-01',
  devtools: { enabled: true },
  css: ['~/assets/css/main.css'],
  vite: {
    plugins: [
      tailwindcss(),
    ],
  },
})

```

* app.vue

```vue
<template>
  <div>
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
  </div>
</template>

```
 