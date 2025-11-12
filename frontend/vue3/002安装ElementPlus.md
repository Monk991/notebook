## [ElementPlust](https://element-plus.gitee.io/zh-CN/guide/installation.html)

### 安装

```bash
PS C:\Users\Monk\Documents\reborn\blog\workspace\blog-frontend> yarn add element-plus
yarn add v1.22.19
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 20 new dependencies.
info Direct dependencies
└─ element-plus@2.3.12
info All dependencies
├─ @ctrl/tinycolor@3.6.1
├─ @element-plus/icons-vue@2.1.0
├─ @floating-ui/core@1.4.1
├─ @floating-ui/dom@1.5.2
├─ @popperjs/core@2.11.7
├─ @types/lodash-es@4.17.9
├─ @types/lodash@4.14.198
├─ @types/web-bluetooth@0.0.16
├─ @vueuse/core@9.13.0
├─ @vueuse/metadata@9.13.0
├─ @vueuse/shared@9.13.0
├─ async-validator@4.2.5
├─ dayjs@1.11.9
├─ element-plus@2.3.12
├─ escape-html@1.0.3
├─ lodash-es@4.17.21
├─ lodash-unified@1.0.3
├─ lodash@4.17.21
├─ memoize-one@6.0.0
└─ normalize-wheel-es@1.2.0
Done in 8.27s.
```

### [按需导入](https://element-plus.gitee.io/zh-CN/guide/quickstart.html#按需导入)

```bash
PS C:\Users\Monk\Documents\reborn\blog\workspace\blog-frontend> npm install -D unplugin-vue-components unplugin-auto-import

added 51 packages, changed 10 packages, and audited 116 packages in 51s

22 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

- vite.config.ts

```ts
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import AutoImport from 'unplugin-auto-import/vite'
import Components from 'unplugin-vue-components/vite'
import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    AutoImport({
      resolvers: [ElementPlusResolver()]
    }),
    Components({
      resolvers: [ElementPlusResolver()]
    })
  ]
})
```

### 验证

```vue
<script setup lang="ts">
const showMsg = () => {
  ElMessage({
    type: 'info',
    message: '提示信息'
  })
}
</script>

<template>
  <el-button @click="showMsg" type="primary">+1</el-button>
</template>
```

### 解决[Cannot find name 'ElMessage'.ts(2304)]

> 在 tsconfig.json 中增加"auto-imports.d.ts"

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "module": "ESNext",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "preserve",

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.d.ts",
    "src/**/*.tsx",
    "src/**/*.vue",
    "auto-imports.d.ts"
  ],
  "references": [{ "path": "./tsconfig.node.json" }]
}
```
