
### [tailwind提示插件插件](https://tailwindcss.com/docs/editor-setup)


## [使用Prettier排序](https://tailwindcss.com/docs/editor-setup#class-sorting-with-prettier)

### 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add -D prettier prettier-plugin-tailwindcss
yarn add v1.22.22
[1/4] 🔍  Resolving packages...
...
$ nuxt prepare
✔ Types generated in .nuxt                                                                             nuxi  11:01:36 AM
✨  Done in 8.19s.
```

### [设置Prettier配置文件](https://prettier.io/docs/configuration.html)

* .prettierrc 

```json
{
  "plugins": ["prettier-plugin-tailwindcss"],
  "printWidth": 100,
  "htmlWhitespaceSensitivity": "ignore",
  "trailingComma": "none"
}
```

* 验证

```vue
<!-- Before -->
<button class="text-white px-4 sm:px-8 py-2 sm:py-3 bg-sky-700 hover:bg-sky-800">Submit</button>

<!-- After -->
<button class="bg-sky-700 px-4 py-2 text-white hover:bg-sky-800 sm:px-8 sm:py-3">Submit</button>
```