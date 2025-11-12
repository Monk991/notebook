## [增加 Shadcn-nuxt](https://www.shadcn-vue.com/docs/installation/nuxt.html)

### 增加 Shadcn-nuxt

```bash
E:\ws-blog\monk-blog>yarn add tailwindcss @tailwindcss/vite
yarn add v1.22.22
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
warning "nuxt > @nuxt/devtools@3.1.0" has unmet peer dependency "vite@>=6.0".
warning "nuxt > unplugin-vue-router@0.16.1" has unmet peer dependency "@vue/compiler-sfc@^3.5.17".
warning "nuxt > @nuxt/devtools > @nuxt/devtools-kit@3.1.0" has unmet peer dependency "vite@>=6.0".
warning "nuxt > @nuxt/devtools > vite-plugin-inspect@11.3.3" has unmet peer dependency "vite@^6.0.0 || ^7.0.0-0".
warning "nuxt > @nuxt/devtools > vite-plugin-vue-tracer@1.1.3" has unmet peer dependency "vite@^6.0.0 || ^7.0.0".
warning "nuxt > @nuxt/devtools > @vue/devtools-core > vite-hot-client@2.1.0" has unmet peer dependency "vite@^2.6.0 || ^3.0.0 || ^4.0.0 || ^5.0.0-0 || ^6.0.0-0 || ^7.0.0-0".
warning "nuxt > @nuxt/devtools > vite-plugin-inspect > vite-dev-rpc@1.1.0" has unmet peer dependency "vite@^2.9.0 || ^3.0.0-0 || ^4.0.0-0 || ^5.0.0-0 || ^6.0.1 || ^7.0.0-0".
warning " > @tailwindcss/vite@4.1.17" has unmet peer dependency "vite@^5.2.0 || ^6 || ^7".
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 8 new dependencies.
info Direct dependencies
└─ @tailwindcss/vite@4.1.17
info All dependencies
├─ @tailwindcss/node@4.1.17
├─ @tailwindcss/oxide-win32-x64-msvc@4.1.17
├─ @tailwindcss/oxide@4.1.17
├─ @tailwindcss/vite@4.1.17
├─ enhanced-resolve@5.18.3
├─ lightningcss-win32-x64-msvc@1.30.2
├─ lightningcss@1.30.2
└─ tapable@2.3.0
$ nuxt prepare
√ Types generated in .nuxt                                                                               nuxi 21:18:48
Done in 19.43s.

E:\ws-blog\monk-blog>npx nuxi@latest module add shadcn-nuxt
Need to install the following packages:
nuxi@3.30.0
Ok to proceed? (y) y

i Resolved shadcn-nuxt, adding module...                                                                 nuxi 21:37:25
i Installing shadcn-nuxt@2.3.2 as a dependency                                                           nuxi 21:37:25
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
success Saved 1 new dependency.
info Direct dependencies
└─ shadcn-nuxt@2.3.2
info All dependencies
└─ shadcn-nuxt@2.3.2
$ nuxt prepare
√ Types generated in .nuxt                                                                               nuxi 21:37:31
Done in 5.43s.
i Adding shadcn-nuxt to the modules                                                                      nuxi 21:37:31

 WARN  Component directory does not exist: E:/ws-blog/monk-blog/app/components/ui                             21:37:32

√ Types generated in .nuxt    
```