## [Mac 安装 GO 语言](https://www.runoob.com/go/go-environment.html)

### 查看系统

```
# lufey @ lufeydeMacBook-Pro in ~ [15:05:23]
$ uname -m
x86_64
```

### [下载](https://go.dev/dl/)

### 安装

- 验证

```bash
$ which go
/usr/local/go/bin/go
```
 
### 使用GOPATH设置项目



* ~/.zshrc

```
export GOPROXY='https://goproxy.cn;direct'
export GOPATH=/Users/lufey/Documents/reborn/notebook/cloudnative/ws-go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

* 设置配置生效

```bash
source ~/.zshrc
```

*  显式地将 GO111MODULE 设置为 "off"， 禁用了Go Modules，使得Go工具会尝试在GOPATH中查找包。

```bash
go env -w GO111MODULE=off
```

### 测试
```
ws-go
--  bin
--  pkg
--  src
    -- learn-project
        --  main.go
        --  lib1
            --  lib1.go
        --  lib2
            --  lib2.go
```

* lib1.go

```go
package lib1

import "fmt"

func Lib1Test(){
	fmt.Println("Lib1Test() ...")
}

func init (){
	fmt.Println("lib1 init")
}
```

* lib2.go

```go
package lib2

import "fmt"

func Lib2Test(){
	fmt.Println("Lib2Test() ...")
}

func init (){
	fmt.Println("lib2 init")
}
```

* main.go
```go
package main


import (
	"learn-project/lib1"
	"learn-project/lib2"
)

func main(){
	lib1.Lib1Test()
	lib2.Lib2Test()
}
```

### 移动到其他目录，
```bash
# lufey @ lufeydeMacBook-Pro in ~/Documents/reborn/notebook/cloudnative/golang/learn-project [10:48:18]
$ go run main.go
main.go:5:2: cannot find package "learn-project/lib1" in any of:
	/usr/local/go/src/learn-project/lib1 (from $GOROOT)
	/Users/lufey/Documents/reborn/notebook/cloudnative/ws-go/src/learn-project/lib1 (from $GOPATH)
main.go:6:2: cannot find package "learn-project/lib2" in any of:
	/usr/local/go/src/learn-project/lib2 (from $GOROOT)
```


* 可以使用go mod
```bash
$ go mod init learn-project
go: modules disabled by GO111MODULE=off; see 'go help modules'

$ go env -w GO111MODULE=''

$ go env
GO111MODULE=''

$ go mod init learn-project
go: creating new go.mod: module learn-project
go: to add module requirements and sums:
	go mod tidy

$ go run main.go
lib1 init
lib2 init
Lib1Test() ...
Lib2Test() ...
```

### [gitee托管](https://www.cnblogs.com/taadis/p/12125807.html)
```
src
	-- gitee.com
		-- monk99
			-- uuid
				-- uuid.go
```


* 初始化mod


* src/gitee.com/monk99/uuid/uuid.go

```go
package uuid

func UUID() int{
	return 1
}
```

```bash
# lufey @ lufeydeMacBook-Pro in ~/Documents/reborn/notebook/cloudnative/ws-go/src/gitee.com/monk99/uuid [11:17:55]
$ go mod init gitee.com/monk99/uuid
go: creating new go.mod: module gitee.com/monk99/uuid
go: to add module requirements and sums:
	go mod tidy
```

```

* 提交代码
```bash
cd uuid
git init 
touch README.md
git add README.md
git commit -m "first commit"
git remote add origin https://gitee.com/monk99/uuid.git
git push -u origin "master"
```

* 打标签
```bash
git push master v0.0.1
```

### 测试
* src/testuuid/main.go

```go
package main

import (
	"fmt"
	"gitee.com/monk99/uuid"
)

func main(){
	i := uuid.UUID()
	fmt.Println('i', i)
}
```

```bash
$ go env -w GO111MODULE=''

$ export GOPRIVATE=gitee.com

$ go mod init
go: creating new go.mod: module testuuid
go: to add module requirements and sums:
	go mod tidy

$ go get gitee.com/monk99/uuid
go: downloading gitee.com/monk99/uuid v0.0.5
go: added gitee.com/monk99/uuid v0.0.5

$ go run main.go
105 1
```