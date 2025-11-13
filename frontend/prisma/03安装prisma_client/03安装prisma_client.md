## [Prisma client](https://www.prisma.io/docs/getting-started/setup-prisma/add-to-existing-project/relational-databases/install-prisma-client-typescript-postgresql)

### 安装

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add @prisma/client
yarn add v1.22.22
[1/4] 🔍  Resolving packages...

...

✔ Types generated in .nuxt                                                                          nuxi  10:33:48 AM
✨  Done in 17.69s.
```

### 命令读取Prisma架构并生成Prisma客户端库

* prisma/schema.prisma

```
generator client {
  provider = "prisma-client-js"
}

...
```

* 生成

```
Monk@LuMonkdeMacBook-Pro blog-portal % yarn prisma generate
yarn run v1.22.22
$ /Users/Monk/Documents/reborn/blog-ws/blog-portal/node_modules/.bin/prisma generate
Environment variables loaded from .env
Prisma schema loaded from prisma/schema.prisma

✔ Generated Prisma Client (v6.5.0) to ./node_modules/@prisma/client in 100ms

Start by importing your Prisma Client (See: https://pris.ly/d/importing-client)

Tip: Want to react to database changes in your app as they happen? Discover how with Pulse: https://pris.ly/tip-1-pulse

✨  Done in 1.99s.
```