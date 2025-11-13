## [Nuxt安装Shadcn](https://www.shadcn-vue.com/docs/installation/nuxt.html)

### 增加tailwind

* 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add -D @nuxtjs/tailwindcss
yarn add v1.22.22
[1/4] 🔍  Resolving packages...

...

✨  Done in 17.32s.
```

* nuxt.config.ts

```ts
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-11-01',
  devtools: { enabled: true },
  modules: [
    '@nuxtjs/tailwindcss'
  ]
})
```

* tailwind.config.js

```js
export default {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

* assets/css/tailwind.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 增加shadcn-nuxt

* 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx nuxi@latest module add shadcn-nuxt
yarn add v1.22.22
[1/4] 🔍  Resolving packages...

...

✨  Done in 10.44s.
```

* nuxt.config.ts

```ts
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-11-01',
  devtools: { enabled: true },
  modules: ['@nuxtjs/tailwindcss', 'shadcn-nuxt'],
  shadcn: {
    /**
     * Prefix for all the imported component
     */
    prefix: 'Ui',
    /**
     * Directory that the component lives in.
     * @default "./components/ui"
     */
    componentDir: './components/ui'
  }
})
```

* Prepare

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx nuxi prepare

✔ Types generated in .nuxt                                                                     nuxi  9:54:37 AM
```

* 初始化客户端

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % npx shadcn-vue@latest init

✔ Preflight checks.
✔ Verifying framework. Found Nuxt.
✔ Validating Tailwind CSS.
✔ Validating import alias.
✔ Which style would you like to use? › New York (Recommended)
✔ Which color would you like to use as the base color? › Neutral
✔ Would you like to use CSS variables for theming? … no / yes
✔ Writing components.json.
✔ Checking registry.
✔ Updating tailwind.config.js
✔ Updating assets/css/tailwind.css

...

You may now add components.
```

### 测试

```vue
<template>
  <div>
    <UiButton>Click me</UiButton>
  </div>
</template>
```
