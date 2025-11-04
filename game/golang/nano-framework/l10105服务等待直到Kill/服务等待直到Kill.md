## 服务等待直到 Kill

- game-frame-nano/internal/game/game.go

```go
package game

import (
	"log/slog"
)

func Startup() {
	slog.Info("Game Startup")
}

```

- game-frame-nano/internal/web/web.go

```go
package web

import (
	"fmt"
	"log/slog"
	"os"
	"os/signal"
	"syscall"
)

func Startup() {
	slog.Info("Web Startup")

	// 新增系统信号Channel
	sg := make(chan os.Signal)
	// 阻塞，直到服务器关闭信号(SIGINT, SIGQUIT, SIGKILL)
	signal.Notify(sg, syscall.SIGINT, syscall.SIGQUIT, syscall.SIGKILL)
	// 阻塞等待信号
	select {
	case s := <-sg:
		slog.Info(fmt.Sprintf("got signal: %s", s.String()))
	}

}

```

- 运行

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
{"timestamp":"2025-07-25 21:37:52.438","level":"INFO","source":{"function":"gitee.com/monk99/game-frame-nano/internal/web.Startup","file":"E:/monk/workspace/game-frame/game-frame-nano/internal/web/web.go","line":12},"msg":"Web Startup"}
{"timestamp":"2025-07-25 21:37:52.438","level":"INFO","source":{"function":"gitee.com/monk99/game-frame-nano/internal/game.Startup","file":"E:/monk/workspace/game-frame/game-frame-nano/internal/game/game.go","line":8},"msg":"Game Startup"}
{"timestamp":"2025-07-25 21:37:56.125","level":"INFO","source":{"function":"gitee.com/monk99/game-frame-nano/internal/web.Startup","file":"E:/monk/workspace/game-frame/game-frame-nano/internal/web/web.go","line":21},"msg":"got signal: interrupt"}
```
