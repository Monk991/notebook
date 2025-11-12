## [Vscode + Prettier]()

### 安装 VsCode 插件[Prettier - Code formatter]

- [VsCode] > [EXTENSIONS] > [Prettier]

### 配置 Prettier

- .prettierrc

```json
{
  "semi": false,
  "singleQuote": true,
  "trailingComma": "none"
}
```

- .prettierignore

```ts
build / node_modules
```

### 设置 VsCode 自动保存格式化

- [VsCode] > [SETTING] > setting.json

```json
{
  // ...
  "[vue]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "editor.formatOnSave": true
}
```
