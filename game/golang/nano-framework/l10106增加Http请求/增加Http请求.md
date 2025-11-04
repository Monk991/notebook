## 增加Http请求

* game-frame-nano/configs/config.toml

```tom
#...

#WEB服务器设置
[webserver]
addr = "0.0.0.0:18080"                         #监听地址
enable_ssl = false                            #是否使用https, 如果为true, 则必须配置cert和key的路径
static_dir = "web/static"
```

* game-frame-nano/internal/web/web.go

```go

package web

import (
	"fmt"
	"log"
	"log/slog"
	"net/http"
	"os"
	"os/signal"
	"syscall"

	"github.com/lonng/nanoserver/pkg/algoutil"
	"github.com/lonng/nex"
	"github.com/spf13/viper"
)

func startupServe() http.Handler {
	var (
		mux = http.NewServeMux()
	)
	mux.Handle("/ping", nex.Handler(pongHandler))

	return algoutil.AccessControl(algoutil.OptionControl(mux))
}

func pongHandler() (string, error) {
	return "pong", nil
}

func Startup() {

	// 启动HTTP服务
	var (
		addr      = viper.GetString("webserver.addr")
		cert      = viper.GetString("webserver.certificates.cert")
		key       = viper.GetString("webserver.certificates.key")
		enableSSL = viper.GetBool("webserver.enable_ssl")
	)

	// 验证必要配置
	if addr == "" {
		slog.Error("webserver.addr is required")
		return
	}

	slog.Info("Web Startup", "addr", addr, "enableSSL", enableSSL)
	go func() {
		mux := startupServe()

		var err error

		if enableSSL {
			if cert == "" || key == "" {
				slog.Error("SSL enabled but cert or key not provided")
				return
			}
			// 启动HTTPS服务
			err = http.ListenAndServeTLS(addr, cert, key, mux)
		} else {
			// 启动HTTP服务
			err = http.ListenAndServe(addr, mux)
		}

		if err != nil && err != http.ErrServerClosed {
			slog.Error("Server error", "error", err)
		}
	}()

	// 新增系统信号Channel,用于监听系统关闭
	// ...
}

```

### 验证

```bash
PS E:\monk\workspace\game-frame\game-frame-nano> curl http://localhost:18080/ping

                                                                                                         
StatusCode        : 200                                                                                  
StatusDescription : OK                                                                                   
Content           : "pong"                                                                               

RawContent        : HTTP/1.1 200 OK
                    Access-Control-Allow-Headers: Origin, Content-Type, Authorization
                    Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
                    Access-Control-Allow-Origin: *
                    Content-Length: 7
                    Co...
Forms             : {}
Headers           : {[Access-Control-Allow-Headers, Origin, Content-Type, Authorization], [Access-Contro
                    l-Allow-Methods, GET, POST, PUT, DELETE, OPTIONS], [Access-Control-Allow-Origin, *],
                     [Content-Length, 7]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : System.__ComObject
RawContentLength  : 7

```