## Nano 增加 mod 支持

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go mod init gitee.com/monk99/game-frame-nano
go: creating new go.mod: module gitee.com/monk99/game-frame-nano
```

### 测试 mod 是否生效

- game-frame-nano/internal/web/web.go

```go
package web

import (
	"fmt"
)

func Startup() {
	fmt.Println("Web Start")
}

```

- game-frame-nano/main.go

```go
package main

import (
	"fmt"

	"gitee.com/monk99/game-frame-nano/internal/web"
)

func main() {
	fmt.Println("Hello world")
	web.Startup()
}

```

- 验证

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go run .\main.go
Hello world
Web Start
```
