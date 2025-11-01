## Go 常用指令

### go build

```bash
PS E:\monk\workspace\goproject\src\go_code\project01> go build .\main.go
PS E:\monk\workspace\goproject\src\go_code\project01> .\main.exe
hello world
```

### go run

```bash
PS E:\monk\workspace\goproject\src\go_code\project01> go run .\main.go
hello world
```

### 代码格式化

```bash
PS E:\monk\workspace\goproject\src\go_code\project01> go fmt .\main.go
main.go
```

### go mod
```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go mod init gitee.com/monk99/game-frame-nano
go: creating new go.mod: module gitee.com/monk99/game-frame-nano
```

### go get
```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go get github.com/spf13/viper
go: downloading github.com/spf13/viper v1.20.1
go: downloading github.com/sagikazarmark/locafero v0.7.0
...
go: added golang.org/x/text v0.21.0
```

### pkg副本

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> go mod vendor
```