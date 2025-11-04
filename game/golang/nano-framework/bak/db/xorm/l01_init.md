## [Xorm Git](https://github.com/go-xorm/xorm)

* db.model.struct.go

```go
package model

import (
	"time"
)

type User struct {
	Id      int64
	Name    string
	Salt    string
	Age     int
	Passwd  string    `xorm:"varchar(200)"`
	Created time.Time `xorm:"created"`
	Updated time.Time `xorm:"updated"`
}

```

* db.model.go

```go
package db

import (
	"fmt"

	"gitee.com/monk99/game-frame-nano/db/model"
	_ "github.com/go-sql-driver/mysql"

	"github.com/go-xorm/xorm"
)

var (
	database *xorm.Engine
)

func Startup() {
	dsn := "root:root1234@tcp(localhost:3306)/game-frame"

	if db, err := xorm.NewEngine("mysql", dsn); err != nil {
		panic(err)
	} else {
		database = db
	}

	err := database.CreateTables(&model.User{})
	if err != nil {
		fmt.Println(err)
		return
	}

	_, err = database.Insert(&model.User{Id: 1, Name: "xlw"})
	if err != nil {
		fmt.Println(err)
		return
	}

	users := make([]model.User, 0)
	err = database.Find(&users)
	if err != nil {
		fmt.Println(err)
		return
	}

	fmt.Println(users)

}

```

* internal/web/web.go

```go
package web

import (
	"fmt"

	"gitee.com/monk99/game-frame-nano/db"
)

func Startup() {
	fmt.Println("Web Start")
	db.Startup()
}

```