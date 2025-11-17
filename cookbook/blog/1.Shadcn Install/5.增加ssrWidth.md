## [增加 ssrWidth](https://www.shadcn-vue.com/docs/installation/nuxt.html)

```bash

E:\ws-blog\monk-blog>yarn add @vueuse/core
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
success Saved 4 new dependencies.
info Direct dependencies
└─ @vueuse/core@14.0.0
info All dependencies
├─ @types/web-bluetooth@0.0.21
├─ @vueuse/core@14.0.0
├─ @vueuse/metadata@14.0.0
└─ @vueuse/shared@14.0.0
$ nuxt prepare

 WARN  Component directory does not exist: E:/ws-blog/monk-blog/app/components/ui                             21:40:30

√ Types generated in .nuxt                                                                               nuxi 21:40:31
Done in 3.17s.
```

- app/plugins/ssr-width.ts

```ts
import { provideSSRWidth } from "@vueuse/core";

export default defineNuxtPlugin((nuxtApp) => {
  provideSSRWidth(1024, nuxtApp.vueApp);
});
```

- nuxt.config.ts

```ts
export default defineNuxtConfig({
  // ...
  modules: ["shadcn-nuxt"],
  shadcn: {
    /**
     * Prefix for all the imported component
     */
    prefix: "",
    /**
     * Directory that the component lives in.
     * @default "./components/ui"
     */
    componentDir: "./components/ui",
  },
});
```
