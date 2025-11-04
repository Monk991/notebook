## Slog

### 初始化 Logger

- game-frame-nano/main.go

```go
package main

import (
	"log/slog"
)

func main() {
	// ...
}

func serve(ctx context.Context, cmd *cli.Command) error {
	// 读取配置文件
	viper.SetConfigType("toml")
	viper.SetConfigFile(cmd.String("config"))
	viper.ReadInConfig()
	// 初始化日志
	initLogger()

	// 启动 web 服务
	web.Startup()

	return nil
}

// 初始化日志
func initLogger() {
	// 设置日志处理选项
	handlerOptions := &slog.HandlerOptions{
		AddSource: true,
		Level:     slog.LevelInfo, // 设置日志级别
		ReplaceAttr: func(groups []string, a slog.Attr) slog.Attr {
			// 如果是时间属性，格式化为指定格式
			if a.Key == "time" {
				return slog.String("timestamp", a.Value.Time().Format("2006-01-02 15:04:05.000"))
			}
			return a
		},
	}

	logFile := viper.GetString("log.file_path")
	// 如果没有配置日志文件路径，则使用默认的标准输出
	if logFile == "" {
		slog.SetDefault(slog.New(slog.NewJSONHandler(os.Stdout, handlerOptions)))
		return
	}

	// 打开日志文件，如果不存在则创建
	fout, err := os.OpenFile(logFile, os.O_CREATE|os.O_WRONLY|os.O_APPEND, 0666)
	if err != nil {
		panic(err)
	}

	// 设置为全局默认logger
	slog.SetDefault(slog.New(slog.NewJSONHandler(fout, handlerOptions)))
}

```

- game-frame-nano/internal/web/web.go

```go
package web

import (
	"log/slog"
)

func Startup() {
	slog.Info("Web package initialized")
}
```

### 验证

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
{"timestamp":"2025-07-25 21:06:04.198","level":"INFO","source":{"function":"gitee.com/monk99/game-frame-nano/internal/web.Start","file":"E:/monk/workspace/game-frame/game-frame-nano/internal/web/web.go","line":8},"msg":"Web package initialized"}
```
