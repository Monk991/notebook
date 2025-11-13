## [Prisma](https://www.prisma.io/docs/getting-started/setup-prisma/add-to-existing-project/relational-databases/connect-your-database-typescript-postgresql)

### 数据库准备

* 创建数据库

```sql
CREATE DATABASE blog
    DEFAULT CHARACTER SET = 'utf8mb4';
```

* 创建用户表

```sql
CREATE TABLE blog_user(  
    id int NOT NULL PRIMARY KEY AUTO_INCREMENT COMMENT 'Primary Key',
    name VARCHAR(255),
    email VARCHAR(255) UNIQUE NOT NULL,
     create_time DATETIME COMMENT 'Create Time'
) COMMENT '';
```

### 连接数据库

* prisma/scheme.prisma

```
datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}
```

* .env

```
DATABASE_URL="mysql://root:root1234@localhost:3306/blog"
```


### 安装prisma

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add prisma
yarn add v1.22.22
[1/4] 🔍  Resolving packages...

...

$ nuxt prepare
✔ Types generated in .nuxt                                                                           nuxi  9:55:38 AM
✨  Done in 32.25s.
```

### 验证

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn prisma db pull
yarn run v1.22.22
$ /Users/Monk/Documents/reborn/blog-ws/blog-portal/node_modules/.bin/prisma db pull
Prisma schema loaded from prisma/schema.prisma
Environment variables loaded from .env
Datasource "db": MySQL database "blog" at "localhost:3306"

✔ Introspected 1 model and wrote it into prisma/schema.prisma in 62ms
      
*** WARNING ***

These objects have comments defined in the database, which is not yet fully supported. Read more: https://pris.ly/d/database-comments
  - Type: "field", name: "blog_user.id"
  - Type: "field", name: "blog_user.create_time"

Run prisma generate to generate Prisma Client.

✨  Done in 1.47s.
```