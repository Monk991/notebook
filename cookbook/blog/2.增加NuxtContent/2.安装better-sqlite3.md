## 启动后提示 ERROR Nuxt Content requires better-sqlite3 module to operate.

```bash
E:\ws-blog\monk-blog> yarn dev
yarn run v1.22.22
$ nuxt dev
  ➜ Local:    http://localhost:3000/
  ➜ Network:  use --host to expose

 ERROR  Nuxt Content requires better-sqlite3 module to operate.
```

### 解决方法

- 安装 better-sqlite3

```bash
E:\ws-blog\monk-blog>yarn add better-sqlite3
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
success Saved 24 new dependencies.
info Direct dependencies
└─ better-sqlite3@12.4.1
info All dependencies
├─ better-sqlite3@12.4.1
├─ bl@4.1.0
├─ chownr@1.1.4
// ...
├─ strip-json-comments@2.0.1
├─ tar-fs@2.1.4
├─ tar-stream@2.2.0
├─ tunnel-agent@0.6.0
└─ wrappy@1.0.2
$ nuxt prepare
√ Types generated in .nuxt                                                                               nuxi 21:22:14
Done in 4.68s.
```
