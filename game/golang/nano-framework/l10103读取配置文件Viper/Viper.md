## [Viper](https://github.com/spf13/viper)

- game-frame-nano/configs/config.toml

```toml
[core]
debug = true
```

- game-frame-nano/configs/config-dev.toml

```toml
[core]
debug = false
```

- game-frame-nano/main.go

```go

package main

import (
	"fmt"
	"context"
	"log"
	"net/mail"
	"os"
	"github.com/spf13/viper"
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
			&cli.StringFlag{
				Name:  "config, c",
				Value: "./configs/config.toml",
				Usage: "load configuration from `FILE`",
			},
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
	// 读取启动参数
	fmt.Println("cpuprofile: ", cmd.Bool("cpuprofile"))

	// 读取配置文件
	viper.SetConfigType("toml")
	viper.SetConfigFile(cmd.String("config"))
	viper.ReadInConfig()

	fmt.Println("core.debug", viper.GetBool("core.debug"))

	web.Startup()

	return nil
}
```

- 安装依赖

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
main.go:9:2: no required module provides package github.com/spf13/viper; to add it:
        go get github.com/spf13/viper

PS E:\monk\workspace\game-frame\game-frame-nano> go get github.com/spf13/viper
go: downloading github.com/spf13/viper v1.20.1
go: downloading github.com/sagikazarmark/locafero v0.7.0
...
go: added golang.org/x/text v0.21.0
```

- 验证

```bash

PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
cpuprofile:  false
core.debug true
Web Start

PS E:\monk\workspace\game-frame\game-frame-nano> go run main.go --config ./configs/config-dev.toml
cpuprofile:  false
core.debug false
Web Start
```
