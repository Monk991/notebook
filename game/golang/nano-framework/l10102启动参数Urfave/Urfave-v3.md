## 启动参数 [urfave/cli:v3](https://cli.urfave.org/v3/getting-started/)

- game-frame-nano/main.go

```go
package main

import (
	"fmt"
	"context"
	"log"
	"net/mail"
	"os"

	"gitee.com/monk99/game-frame-nano/internal/web"
	"github.com/urfave/cli/v3"
)

func main() {

	cmd := &cli.Command{
		Name: "game-frame-nano",
		Authors: []any{
			mail.Address{Name: "Monk", Address: "monk99_1@163.com"},
		},
		Version: "1.0.0",
		Usage:   "game-frame-nano",
		Flags: []cli.Flag{
			&cli.BoolFlag{
				Name:  "cpuprofile",
				Usage: "enable cpu profile",
			},
		},

		Action: serve,
	}

	if err := cmd.Run(context.Background(), os.Args); err != nil {
		log.Fatal(err)
	}
}

func serve(ctx context.Context,cmd *cli.Command) error {
	fmt.Println("cpuprofile: ", cmd.Bool("cpuprofile"))

	web.Startup()

	return nil
}
```

### 安装依赖

- 如果下载慢，可以设置 GO 模块镜像

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go env -w GOPROXY=https://goproxy.cn,direct
```

- 安装依赖

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go get github.com/urfave/cli/v3
go: downloading github.com/urfave/cli v1.22.17
go: downloading github.com/urfave/cli/v3 v3.3.8
go: added github.com/urfave/cli/v3 v3.3.8
```

### 运行

- 增加参数

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
cpuprofile:  false
Web Start

PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go --cpuprofile
cpuprofile:  true
Web Start

PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go --cpuprofile=true
cpuprofile:  true
Web Start
```

- 查看帮助

```
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go -h
NAME:
   game-frame-nano - game-frame-nano

USAGE:
   game-frame-nano [global options]

VERSION:
   1.0.0

AUTHOR:
   {Monk monk99_1@163.com}

GLOBAL OPTIONS:
   --cpuprofile   enable cpu profile (default: false)
   --help, -h     show help
   --version, -v  print the version
```
