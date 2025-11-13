## [DarkMode](https://www.shadcn-vue.com/docs/dark-mode/nuxt.html)

* 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add -D @nuxtjs/color-mode

yarn add v1.22.22

...

✨  Done in 7.57s.
```

* nuxt.config.ts

```ts
// https://nuxt.com/docs/api/configuration/nuxt-config
export default defineNuxtConfig({
  compatibilityDate: '2024-11-01',
  devtools: { enabled: true },
  modules: ['@nuxtjs/tailwindcss', 'shadcn-nuxt', '@nuxtjs/color-mode'],
  shadcn: {
    prefix: '',
    componentDir: './components/ui'
  },
  colorMode: {
    classSuffix: ''
  }
})
```